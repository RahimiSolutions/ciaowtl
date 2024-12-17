<script lang="ts">
	import Lenis from 'lenis';
	import 'lenis/dist/lenis.css';
	import { onDestroy, onMount } from 'svelte';
	import Button from '../components/buttons/button.svelte';

	import shipping from '$lib/images/transport.jpeg';

	import { quintOut } from 'svelte/easing';
	import { fade, fly } from 'svelte/transition';
	import Topnotch from '../components/notches/topnotch.svelte';
	import Cornernotch from '../components/notches/cornernotch.svelte';

	let lenis: Lenis | null = null;
	let notches = false;
	let bgImage = false;

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

		bgImage = true;
		setTimeout(() => {
			notches = true;
		}, 300); // Adjust delay as needed
	});

	onDestroy(() => {
		if (lenis) {
			lenis.destroy();
		}
	});
</script>

<div class="container">
	<div class="hero">
		<div class="content-wrapper">
			<div class="background">
				{#if bgImage}
					<div class="bg-image" transition:fade={{ delay: 0, duration: 800 }}>
						<img src={shipping} alt="" />
						<div class="bg-overlay"></div>
					</div>
				{/if}

				{#if notches}
					<Topnotch />
					<Cornernotch />
				{/if}
			</div>

			<div class="top-menu"></div>
			<div class="text">
				<div class="main-heading"></div>
				<div class="sub-heading"></div>
			</div>
			<div class="cta"></div>
		</div>
	</div>
</div>

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
				}
			}
		}
	}
</style>
