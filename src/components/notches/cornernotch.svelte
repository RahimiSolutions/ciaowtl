<script lang="ts">
	import cornerNotch from '$lib/images/corner-notch.svg';
	import cta from '$lib/images/cta.png';
	import { quintOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import { goto } from '$app/navigation';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';
	let logo = false;

	function handleClick() {
		window.open('https://wa.me/4917657966211?text=Hi%20Ciao-team%2C%20I%20want%20to%20request%20a%20quote%20from%20%5Bcity%2C%20country%5D%20to%20%5Bcity%2C%20country%5D%0ABest%20regards%2C%0A%5BYour%20Name%5D', '_blank');
	}

	onMount(() => {
		setTimeout(() => {
			logo = true;
		}, 400); // delay
	});
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<div class="notch">
			<div
				class="corner-notch"
				transition:fly={{ y: 50, delay: 300, duration: 1000, easing: quintOut }}
			>
				<img class="cornernotch-svg" src={cornerNotch} alt="" />

				{#if logo}
					<div class="cta" transition:fly={{ y: 50, delay: 300, duration: 1000, easing: quintOut }}>
						<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_noninteractive_element_interactions -->
						<img onclick={handleClick} src={cta} alt="" />
					</div>
				{/if}
			</div>
		</div>
	{/if}
</MediaQuery>
<MediaQuery query="(max-width: 1023px)" let:matches>
	{#if matches}
		<div class="mobile-notch">
			<div
				class="corner-notch"
				transition:fly={{ y: 50, delay: 300, duration: 1000, easing: quintOut }}
			>
				<img class="cornernotch-svg" src={cornerNotch} alt="" />

				{#if logo}
					<div class="cta" transition:fly={{ y: 50, delay: 300, duration: 1000, easing: quintOut }}>
						<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_noninteractive_element_interactions -->
						<img onclick={handleClick} src={cta} alt="" />
					</div>
				{/if}
			</div>
		</div>
	{/if}
</MediaQuery>

<style lang="scss">
	.notch {
		width: 100%;
		display: flex;
		justify-content: end;
		align-items: start;
		background-color: white;

		.corner-notch {
			position: absolute;
			width: fit-content;
			display: flex;
			justify-content: center;
			align-items: start;
			position: absolute;
			z-index: 99;
			bottom: 0px;
			right: 0px;
			.cta {
				position: absolute;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: end;
				bottom: 10%;
				left: 20%;

				img {
					max-width: 150%;
					transition: 0.2s ease-in-out;
					&:hover {
						scale: 1.01;
						cursor: pointer;
					}
				}
			}
		}
	}
	.mobile-notch {
		width: 100%;
		display: flex;
		justify-content: end;
		align-items: start;
		background-color: white;

		.corner-notch {
			position: absolute;
			width: fit-content;
			display: flex;
			justify-content: center;
			align-items: start;
			position: absolute;
			z-index: 99;
			bottom: -1px;
			right: -1px;

			.cornernotch-svg {
				width: 250px;
			}
			.cta {
				position: absolute;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: end;
				bottom: 10%;
				left: 10%;

				img {
					max-width: 80%;
					transition: 0.2s ease-in-out;
					&:hover {
						scale: 1.01;
						cursor: pointer;
					}
				}
			}
		}
	}
</style>
