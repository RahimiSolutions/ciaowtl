<script lang="ts">
	import topNotch from '$lib/images/top-notch.svg';
	import ciaowtl from '$lib/images/logo.png';
	import { quintOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';
	let logo = false;

	onMount(() => {
		setTimeout(() => {
			logo = true;
		}, 400); // Adjust delay as needed
	});
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<div class="notch">
			<div
				class="top-notch"
				transition:fly={{ y: -50, delay: 300, duration: 1000, easing: quintOut }}
			>
				<img class="topnotch-svg" src={topNotch} alt="Scalable vector graphic of top notch" />

				{#if logo}
					<div
						class="logo"
						transition:fly={{ y: -50, delay: 300, duration: 1000, easing: quintOut }}
					>
						<img src={ciaowtl} alt="Ciao World Transport & Logisitics Logo" />
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
				class="top-notch"
				transition:fly={{ y: -50, delay: 300, duration: 1000, easing: quintOut }}
			>
				<img class="topnotch-svg" src={topNotch} alt="Scalable vector graphic of top notch" />

				{#if logo}
					<div
						class="logo"
						transition:fly={{ y: -50, delay: 300, duration: 1000, easing: quintOut }}
					>
						<img src={ciaowtl} alt="Ciao World Transport & Logisitics Logo" />
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
		justify-content: center;
		align-items: start;
		background-color: white;

		.top-notch {
			width: fit-content;
			display: flex;
			justify-content: center;
			align-items: start;
			position: absolute;
			z-index: 99;
			top: 0;

			.logo {
				position: absolute;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				img {
					max-width: 60%;
				}
			}
		}
	}
	.mobile-notch {
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: start;
		background-color: white;

		.top-notch {
			width: fit-content;
			display: flex;
			justify-content: center;
			align-items: start;
			position: absolute;
			z-index: 99;
			top: 0;

			.topnotch-svg {
				width: 225px;
			}
			.logo {
				position: absolute;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				img {
					max-width: 60%;
				}
			}
		}
	}
</style>
