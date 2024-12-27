<script lang="ts">
	import Lenis from 'lenis';
	import 'lenis/dist/lenis.css';
	import { onDestroy, onMount } from 'svelte';
	import { fade, fly } from 'svelte/transition';
	import shipping from '$lib/images/transport.jpg';
	import Topnotch from '../components/notches/topnotch.svelte';
	import Cornernotch from '../components/notches/cornernotch.svelte';
	import MediaQuery from '../components/MediaQuery/MediaQuery.svelte';
	import { quintOut } from 'svelte/easing';
	import TransportTypeContainer from '../components/containers/transportTypeContainer.svelte';
	import Button from '../components/buttons/button.svelte';
	import ReviewContainer from '../components/containers/reviewContainer.svelte';
	import BenefitCard from '../components/cards/benefitCard.svelte';

	import partner from '$lib/images/handshake.jpg';
	import processPicture from '$lib/images/process.jpg';
	import multilingual from '$lib/images/multilingual.jpg';
	import multilingualOpt from '$lib/images/multilingual_opt.jpg';

	let lenis: Lenis | null = null;
	let notches = false;
	let bgImage = false;
	let textVisible = false;

	onMount(() => {
		lenis = new Lenis({
			duration: 1.3,
			easing: (t) => Math.min(1, 1.001 - Math.pow(2, -10 * t)),
			touchMultiplier: 2,
			infinite: false
		});

		function raf(time: any) {
			lenis?.raf(time);
			requestAnimationFrame(raf);
		}

		requestAnimationFrame(raf);

		setTimeout(() => {
			bgImage = true;
		}, 200);

		setTimeout(() => {
			notches = true;
		}, 300);

		setTimeout(() => {
			textVisible = true;
		}, 1500);
	});

	onDestroy(() => {
		if (lenis) {
			lenis.destroy();
		}
	});
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<div class="container">
			<div class="hero">
				<div class="content-wrapper">
					<div class="background">
						{#if bgImage}
							<div class="bg-image" transition:fade={{ delay: 0, duration: 500 }}>
								<img loading="lazy" src={shipping} alt="" />
								<div class="bg-overlay"></div>
							</div>
						{/if}

						{#if notches}
							<Topnotch />
							<Cornernotch />
						{/if}
						{#if textVisible}
							<div
								class="text"
								transition:fly={{ y: 50, delay: 300, duration: 500, easing: quintOut }}
							>
								<div class="main-heading">
									<span class="top">Stress Free</span> <br />
									<span class="bottom"
										>Transport Services
										<div class="sub-heading">
											We operate globally, connecting major cities and remote locations alike
										</div></span
									>
								</div>
							</div>
						{/if}
					</div>
				</div>
			</div>

			<div class="options">
				<div class="left">
					<div class="top">
						<h1>Transport Made Easy</h1>
						<p>
							No matter where your cargo needs to go, we have the infrastructure to deliver it
							effectively.
						</p>
					</div>
					<div class="bottom">
						<ReviewContainer />
					</div>
				</div>
				<div class="right">
					<TransportTypeContainer />
					<div class="content">
						<div class="title">Your transport & Logistics partner</div>
						<div class="text">
							From A to Z, we handle your shipments with care and precision.<br /> Reliable, multilingual,
							and committed to your success.
						</div>
						<div class="button"><Button text="Request a Quote" borderRadius="5px" /></div>
					</div>
				</div>
			</div>

			<div class="about">
				<div class="top">
					<div class="title"><h2>Why Choose Us?</h2></div>
					<div class="text">
						<p>At Ciao World, our mission is to simplify your logistics and earn your trust.</p>
					</div>
				</div>
				<div class="content">
					<BenefitCard
						title="Reliable<br/>Partner"
						text="You can trust us to deliver on time, every time"
						imageUrl={partner}
					/>
					<BenefitCard
						title="Multilingual<br/>Expertise"
						text=" Communication without barriers"
						imageUrl={multilingual}
					/>
					<BenefitCard
						title="Seamless<br/>Process"
						text="We handle the complexities so you don’t have to"
						imageUrl={processPicture}
					/>
				</div>
				<div class="button">
					<Button text="Learn More" borderRadius="5px" />
				</div>
			</div>
		</div>
	{/if}
</MediaQuery>

<style lang="scss">
	.container {
		.hero {
			.content-wrapper {
				.background {
					position: relative;
					width: 98%;
					height: 90vh;
					overflow: hidden;
					border-radius: 50px;
					margin: 25px auto 25px auto;
					.bg-image {
						position: relative;
						height: 100%;
						width: 100%;
						img {
							border-radius: 50px;
							left: 50%;
							transform: translateX(-50%);
							position: absolute;
							height: 100%;
							z-index: 0;
						}
						.bg-overlay {
							position: relative;
							background-color: var(--green-200);
							width: 100%;
							height: 100%;
						}
					}

					.text {
						position: absolute;
						bottom: 8%;
						left: 4%;

						.main-heading {
							font-size: var(--fs-800);
							font-weight: 600;
							color: var(--white);
							.top {
								backdrop-filter: blur(4px);
								background-color: var(--blue-200);
								border-radius: 25px 25px 0 0;
								padding: 0 24px;
							}
							.bottom {
								backdrop-filter: blur(4px);
								background-color: var(--blue-200);
								border-radius: 0 25px 25px 25px;
								padding: 0 24px;
								display: flex;
								flex-direction: column;
								padding-bottom: 8px;
								.sub-heading {
									font-size: var(--fs-400);
									font-weight: 800;
									color: var(--white);
									text-transform: uppercase;
								}
							}
						}
					}
				}
			}
		}
		.options {
			width: 98%;
			margin: 0 auto;
			display: flex;
			margin-bottom: 200px;
			align-items: stretch;
			.left {
				height: auto;
				width: 30%;
				padding: 0 50px;
				display: flex;
				flex-direction: column;
				justify-content: space-between;
				.top {
					h1 {
						font-size: var(--fs-800);
						font-weight: 600;
						color: var(--black);
					}
					p {
						font-size: var(--fs-500);
						font-weight: 400;
						color: var(--black);
					}
				}
			}
			.right {
				width: 70%;
				display: flex;
				flex-direction: column;
				justify-content: start;
				overflow: hidden;

				.content {
					margin-top: 8px;
					display: flex;
					flex-direction: column;
					align-items: end;
					width: 100%;

					.title {
						font-size: var(--fs-600);
						font-weight: 400;
						text-transform: uppercase;
						color: var(--green-500);
						max-width: 40ch;
						text-align: end;
					}
					.text {
						margin-top: 16px;
						font-size: var(--fs-500);
						font-weight: 400;
						color: var(--black);
						max-width: 50ch;
						text-align: end;
					}
					.button {
						margin-top: 36px;
					}
				}
			}
		}
		.about {
			width: 70%;
			margin: auto;
			.top {
				display: flex;
				flex-direction: column;
				align-items: start;
				justify-content: start;
				margin-bottom: 50px;
				.title {
					h2 {
						font-size: var(--fs-600);
						font-weight: 900;
						color: var(--green-500);
						text-transform: uppercase;
					}
				}
				.text {
					font-size: var(--fs-500);
					font-weight: 500;
					color: var(--black);
					max-width: 60ch;
					text-align: start;
				}
			}
			.content{
				display: flex;
				justify-content: space-between;
			}
			.button{
				width: 100%;
				display: flex;
				justify-content: end;
				margin-top: 36px;
			}
		}
	}
</style>
