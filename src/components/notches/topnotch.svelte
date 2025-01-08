<script lang="ts">
	import topNotch from '$lib/images/top-notch.svg';
	import ciaowtl from '$lib/images/logo.png';
	import { quintOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	let logo = false;

	onMount(() => {
		setTimeout(() => {
			logo = true;
		}, 400); // Adjust delay as needed
	});
</script>

<div class="notch">
	<div class="top-notch" transition:fly={{ y: -50, delay: 300, duration: 1000, easing: quintOut }}>
		<img class="topnotch-svg" src={topNotch} alt="Scalable vector graphic of top notch" />

		{#if logo}
			<div class="logo" transition:fly={{ y: -50, delay: 300, duration: 1000, easing: quintOut }}>
				<img src={ciaowtl} alt="Ciao World Transport & Logisitics Logo" />
			</div>
		{/if}
	</div>
</div>

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

			.topnotch-svg{
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
