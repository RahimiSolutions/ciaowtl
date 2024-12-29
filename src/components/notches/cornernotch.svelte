<script lang="ts">
	import cornerNotch from '$lib/images/corner-notch.svg';
	import cta from '$lib/images/cta.png';
	import { quintOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import { goto } from '$app/navigation';
	let logo = false;

	function handleClick() {
		window.open('https://wa.me/4917657966211', '_blank');
	}

	onMount(() => {
		setTimeout(() => {
			logo = true;
		}, 400); // Adjust delay as needed
	});
</script>

<div class="notch">
	<div
		class="corner-notch"
		transition:fly={{ y: 50, delay: 300, duration: 1000, easing: quintOut }}
	>
		<img src={cornerNotch} alt="" />

		{#if logo}
			<div class="cta"  transition:fly={{ y: 50, delay: 300, duration: 1000, easing: quintOut }}>
				<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_noninteractive_element_interactions -->
				<img onclick={handleClick} src={cta} alt="" />
			</div>
		{/if}
	</div>
</div>

<style lang="scss">
	.notch {
		width: 100%;
		display: flex;
		justify-content: end;
		align-items: start;
		background-color: white;
	}
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
</style>
