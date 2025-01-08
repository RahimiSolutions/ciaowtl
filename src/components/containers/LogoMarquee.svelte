<script>
	import ciao from '$lib/images/logo.png';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';
	/**
	 * @type {HTMLElement}
	 */
	let wrapper; // Reference to the wrapper element
	/**
	 * @type {HTMLDivElement}
	 */
	let marquee1; // Reference to the first marquee
	/**
	 * @type {HTMLDivElement}
	 */
	let marquee2; // Reference to the second marquee

	export let imgSize = '75px';
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<article class="wrapper" bind:this={wrapper} style="--imgSize: {imgSize};">
			<div class="marquee" bind:this={marquee1}>
				<div class="marquee__group">
					<img src={ciao} alt="Sarpsborg Moske" />
					<img src={ciao} alt="CiaoWTL" />
					<img src={ciao} alt="Brightpath Studio" />
				</div>
				<div aria-hidden="true" class="marquee__group">
					<img src={ciao} alt="Sarpsborg Moske" />
					<img src={ciao} alt="CiaoWTL" />
					<img src={ciao} alt="Brightpath Studio" />
				</div>
			</div>
		</article>
	{/if}
</MediaQuery>
<MediaQuery query="(max-width: 1023px)" let:matches>
	{#if matches}
		<article class="mobile-wrapper" bind:this={wrapper} style="--imgSize: {imgSize};">
			<div class="marquee" bind:this={marquee1}>
				<div class="marquee__group">
					<img src={ciao} alt="Sarpsborg Moske" />
					<img src={ciao} alt="CiaoWTL" />
					<img src={ciao} alt="Brightpath Studio" />
				</div>
				<div aria-hidden="true" class="marquee__group">
					<img src={ciao} alt="Sarpsborg Moske" />
					<img src={ciao} alt="CiaoWTL" />
					<img src={ciao} alt="Brightpath Studio" />
				</div>
			</div>
		</article>
	{/if}
</MediaQuery>

<style lang="scss">
	:root {
		--size: clamp(5rem, 1rem + 40vmin, 15rem);
		--gap: calc(var(--size) / 4);
		--duration: 60s;
		--scroll-start: 0;
		--scroll-end: calc(-100% - var(--gap));
	}

	* {
		box-sizing: border-box;
	}

	.wrapper {
		display: flex;
		flex-direction: column;
		gap: var(--gap);
		margin: auto;
		margin-top: 50px;
		max-width: 100vw;

		.marquee {
			display: flex;
			overflow: hidden;
			user-select: none;
			gap: var(--gap);
			mask-image: linear-gradient(
				var(--mask-direction, to right),
				hsl(0 0% 0% / 0),
				hsl(0 0% 0% / 1) 20%,
				hsl(0 0% 0% / 1) 80%,
				hsl(0 0% 0% / 0)
			);

			&__group {
				flex-shrink: 0;
				display: flex;
				align-items: center;
				justify-content: space-around;
				gap: var(--gap);
				min-width: 100%;
				animation: scroll-x var(--duration) linear infinite;

				img {
					max-height: var(--imgSize);
				}
			}

			/* Reverse scrolling (if needed) */
			/* &--reverse {
				& .marquee__group {
					animation-direction: reverse;
					animation-delay: -3s;
				}
			} */

			@media (prefers-reduced-motion: reduce) {
				&__group {
					animation-play-state: paused;
				}
			}
		}
	}
	.mobile-wrapper {
		display: flex;
		flex-direction: column;
		gap: var(--gap);
		margin: auto;
		max-width: 100vw;

		.marquee {
			display: flex;
			overflow: hidden;
			user-select: none;
			gap: var(--gap);
			mask-image: linear-gradient(
				var(--mask-direction, to right),
				hsl(0 0% 0% / 0),
				hsl(0 0% 0% / 1) 20%,
				hsl(0 0% 0% / 1) 80%,
				hsl(0 0% 0% / 0)
			);

			&__group {
				flex-shrink: 0;
				display: flex;
				align-items: center;
				justify-content: space-around;
				gap: var(--gap);
				min-width: 100%;
				animation: scroll-x var(--duration) linear infinite;

				img {
					max-height: var(--imgSize);
				}
			}

			/* Reverse scrolling (if needed) */
			/* &--reverse {
				& .marquee__group {
					animation-direction: reverse;
					animation-delay: -3s;
				}
			} */

			@media (prefers-reduced-motion: reduce) {
				&__group {
					animation-play-state: paused;
				}
			}
		}
	}

	@keyframes scroll-x {
		from {
			transform: translateX(var(--scroll-start));
		}
		to {
			transform: translateX(var(--scroll-end));
		}
	}

	@keyframes scroll-y {
		from {
			transform: translateY(var(--scroll-start));
		}
		to {
			transform: translateY(var(--scroll-end));
		}
	}
</style>
