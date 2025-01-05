<script lang="ts">
	import { asClassComponent } from 'svelte/legacy';
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
	import wave from '$lib/images/wave-green.svg';
	import ServiceCard from '../components/cards/serviceCard.svelte';
	import notchCorner from '$lib/images/corner-notch.svg';
	import ReviewsWidget from '../components/containers/reviewsWidget.svelte';
	import LogoMarquee from '../components/containers/LogoMarquee.svelte';
	import cornerNotchGreen from '$lib/images/corner-notch-green.svg';
	import ContactCard from '../components/cards/contactCard.svelte';
	import ContainerCarousel from '../components/containers/containerCarousel.svelte';

	let lenis: Lenis | null = null;
	let notches = false;
	let bgImage = false;
	let textVisible = false;
	let flipAll = false;

	function handleFlipAll() {
		flipAll = !flipAll;
	}

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
			<div class="hero" id="home">
				<div class="content-wrapper">
					<div class="background">
						{#if bgImage}
							<div class="bg-image" transition:fade={{ delay: 100, duration: 1000 }}>
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
									<div class="toptext">Stress Free</div>

									<div class="bottomtext">
										Transport Services
										<div class="sub-heading">
											We operate globally, connecting major cities and remote locations alike
										</div>
									</div>
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
						<div class="button">
							<Button
								text="Request a Quote"
								borderRadius="5px"
								link="https://wa.me/4917657966211"
							/>
						</div>
					</div>
				</div>
			</div>
			<hr />
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
					<Button text="Learn More" borderRadius="5px" link="https://wa.me/4917657966211" />
				</div>
			</div>

			<div class="services" id="services">
				<img src={wave} alt="" />
				<div class="content">
					<div class="text">
						<div class="title"><h1>Comprehensive Logistics Solutions</h1></div>
						<div class="subtitle">
							<p>We provide end-to-end transport services tailored to your needs.</p>
						</div>
					</div>
					<div class="cards">
						<div class="card" id="Truck"><ServiceCard title="Truck" flipped={flipAll} /></div>
						<div class="card" id="Air"><ServiceCard title="Air" flipped={flipAll} /></div>
						<div class="card" id="Ship"><ServiceCard title="Ship" flipped={flipAll} /></div>
						<div class="card" id="Rail"><ServiceCard title="Rail" flipped={flipAll} /></div>
						<div class="card" id="Import"><ServiceCard title="Import" flipped={flipAll} /></div>
						<div class="card" id="Export"><ServiceCard title="Export" flipped={flipAll} /></div>
						<div class="card" id="Project"><ServiceCard title="Project" flipped={flipAll} /></div>
						<div class="card" id="Breakbulk">
							<ServiceCard title="Breakbulk" flipped={flipAll} />
						</div>
					</div>
					<div class="explore">
						<img src={notchCorner} alt="" />
						<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_static_element_interactions -->
						<div class="button">
							<Button text="Explore All Services" borderRadius="5px" onClick={handleFlipAll} />
						</div>
					</div>
				</div>
			</div>

			<div class="social-proof">
				<div class="text">
					<div class="tag">
						<p>You can trust us to deliver your shipment <span class="bold">safely</span></p>
					</div>
					<div class="title">
						<h1>
							Don’t just take our word for it<br />
							<span class="bold">- Here’s what our clients have to say</span>
						</h1>
					</div>
					<div class="vr"></div>
				</div>
				<!-- <ReviewsWidget /> -->
				<div class="review-widget" id="reviews">
					<script src="https://static.elfsight.com/platform/platform.js" async></script>
					<div
						class="elfsight-app-b236145a-e48d-457c-a568-c24604f49d7c"
						data-elfsight-app-lazy
					></div>
				</div>

				<div class="stats">
					<div class="vr"></div>
					<div class="stats-grid">
						<div class="grid-item">
							<div class="number">150+</div>
							<div class="text">
								<span class="highlight">Happy Clients</span> Served Internationally
							</div>
						</div>
						<div class="grid-item">
							<div class="number">35+</div>
							<div class="text">Years Combined <span class="highlight">Experience</span></div>
						</div>

						<div class="grid-item">
							<div class="number">5/5</div>
							<div class="text"><span class="highlight">Stars Rated</span> By our Clients</div>
						</div>
						<div class="grid-item">
							<div class="number">780+</div>
							<div class="text">Shipments<span class="highlight">Successfully Delivered</span></div>
						</div>
					</div>
					<hr />
				</div>

				<div class="partners">
					<div class="text">
						<p>
							With the help from <span class="highlight">our trusted partners</span>, we make sure
							to deliver your shipment <span class="highlight">safely and securely</span>
						</p>
					</div>
					<div class="partner-marquee">
						<LogoMarquee />
						<img src={cornerNotchGreen} alt="" />
					</div>
				</div>
			</div>

			<div class="containers" id="containers">
				<ContainerCarousel />
			</div>

			<div class="contact" id="contact">
				<div class="title"><h1>Contact our friendly team</h1></div>
				<div class="subtitle"><p>Let us know how we can help</p></div>

				<div class="contact-cards">
					<ContactCard type="email" />
					<ContactCard type="address" />
					<ContactCard type="phone" />
				</div>
			</div>
		</div>
	{/if}
</MediaQuery>

<style lang="scss">
	.container {
		hr {
			background-color: var(--white);
			border-top: 1px solid var(--green-400);
		}
		.hero {
			.content-wrapper {
				.background {
					position: relative;
					max-width: 2400px;
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
							display: flex;
							flex-direction: column;

							.toptext {
								backdrop-filter: blur(4px);
								background-color: rgba(67, 86, 100, 0.3);
								border-radius: 25px 25px 0 0;
								padding: 0 24px;
								width: fit-content;
							}
							.bottomtext {
								backdrop-filter: blur(8px);
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
			max-width: 2400px;
			width: 98%;
			margin: 0 auto;
			display: flex;
			margin-bottom: 100px;
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
						max-width: 60%;
						text-align: end;
					}
					.text {
						margin-top: 16px;
						font-size: var(--fs-500);

						font-weight: 400;
						color: var(--black);
						max-width: 60%;
						text-align: end;
					}
					.button {
						margin-top: 36px;
					}
				}
			}
		}
		.about {
			width: 90%;
			max-width: 1600px;
			margin: 100px auto 0 auto;
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
			.content {
				display: flex;
				justify-content: space-between;
			}
			.button {
				width: 100%;
				display: flex;
				justify-content: end;
				margin-top: 36px;
			}
		}

		.services {
			margin: 0;
			position: relative;
			display: flex;
			flex-direction: column;
			img {
				width: 100%;
				margin-bottom: -2px;
			}
			.content {
				width: 100%;
				background-color: var(--green-600);
				.text {
					color: var(--white);
					text-align: center;
					.title {
						text-transform: uppercase;
						h1 {
							font-weight: 900;
						}
						font-size: var(--fs-400);
						margin-bottom: 16px;
					}

					.subtitle {
						font-size: var(--fs-500);
						font-weight: 300;
					}
				}
				.cards {
					width: 90%;
					max-width: 1600px;
					margin: 150px auto;
					display: grid;
					grid-template-columns: repeat(2, 1fr);
					gap: 100px;
					.card {
						scroll-margin-top: 120px;
						display: flex;
						justify-content: center;
					}
				}

				.explore {
					bottom: 0;
					right: 0;
					position: absolute;
					img {
						position: absolute;
						width: 500px;
						bottom: 0px;
						right: 0px;
						z-index: 2;
					}
					.button {
						left: -35%;
						margin-bottom: 10%;
						position: relative;
						z-index: 3;
					}
				}
			}
		}

		.social-proof {
			.text {
				display: flex;
				flex-direction: column;
				width: 100%;
				margin: auto;
				padding-bottom: 24px;
				position: relative;
				.vr {
					position: absolute;
					left: 50%;
					transform: translateX(-50%);
					height: 100%;
					border-left: 1px solid var(--green-400);
				}
				.tag {
					display: flex;
					justify-content: end;
					margin-top: 100px;
					margin-bottom: 16px;
					width: 50%;
					p {
						padding-right: 8px;
						font-size: var(--fs-600);
						color: var(--green-500);
						font-weight: 500;
						text-align: end;
						.bold {
							font-size: var(--fs-600);
							color: var(--green-500);
							font-weight: 900;
						}
					}
				}
				.title {
					display: flex;
					width: 50%;
					transform: translateX(100%);
					h1 {
						padding-left: 8px;
						text-align: start;

						font-weight: 400;
						font-size: var(--fs-500);
						.bold {
							font-size: var(--fs-600);
							color: var(--green-500);
							font-weight: 900;
						}
					}
				}
			}
			.review-widget {
				scroll-margin-top: 200px;
				padding: 100px 0 50px 0;
				background-color: var(--green-500);
			}
			.stats {
				position: relative;
				.vr {
					position: absolute;
					left: 50%;
					transform: translateX(-50%);
					height: 100%;
					border-left: 1px solid var(--green-400);
				}
				.stats-grid {
					display: grid;
					grid-template-columns: repeat(2, 1fr);
					gap: 20px;
					padding-top: 50px;
				}
				.grid-item {
					display: flex;
					flex-direction: column;
					align-items: center;
					justify-content: center;
					padding: 20px;
					border-radius: 10px;
				}
				.number {
					font-size: var(--fs-800);
					font-weight: bold;
					color: var(--black);
				}
				.text {
					font-weight: 600;
					font-size: var(--fs-600);
					color: var(--black);
					margin-top: 8px;
					text-align: center;
					.highlight {
						color: var(--green-500);
					}
				}
			}
			.partners {
				margin: 200px 0;
				.text {
					font-size: var(--fs-600);
					width: 80%;
					text-align: start;
					margin-bottom: 36px;
					p {
						width: 40ch;
					}
					.highlight {
						color: var(--green-500);
					}
				}
				.partner-marquee {
					padding: 50px 0;
					background-color: var(--green-600);
					position: relative;
					img {
						position: absolute;
						top: 99%;
						right: 0;
						rotate: 180deg;
						transform: scaleX(-1);
					}
				}
			}
		}
		.contact {
			scroll-margin-top: 200px;
			.title {
				h1 {
					font-weight: 900;
					font-size: var(--fs-600);
					color: var(--green-500);
					text-align: center;
				}
			}
			.subtitle {
				margin-top: 8px;
				p {
					font-size: var(--fs-500);
					text-align: center;
				}
			}
			.contact-cards {
				display: flex;
				justify-content: space-evenly;

				max-width: 2400px;
				margin: 50px auto;
			}
		}
	}
</style>
