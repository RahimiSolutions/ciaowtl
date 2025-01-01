<script lang="ts">
	import { quintOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';
	import { goto } from '$app/navigation';

	let showTopMenu: boolean;
	let activeItem = 'Home';
	let navigationOn = false;

	function handleScroll() {
		const scrollY = window.scrollY;
		const documentHeight = document.documentElement.scrollHeight;
		const windowHeight = window.innerHeight;
		const past500px = scrollY > 800;
		// const nearBottom = scrollY + windowHeight >= documentHeight - 800;
		// Show the BookingCta only if scrolled past 500px from the top and not near the bottom
		showTopMenu = past500px;
	}

	function handleClick(item: string, link: string) {
		activeItem = item;
		goto(link);
	}

	onMount(() => {
		window.addEventListener('scroll', handleScroll, { passive: true });

		setTimeout(() => {
			navigationOn = true;
		}, 200); // Adjust delay as needed
	});
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_noninteractive_element_interactions -->
		{#if !showTopMenu}
			{#if navigationOn}
				<nav
					class="hero-menu"
					transition:fly={{ y: -50, delay: 300, duration: 600, easing: quintOut }}
				>
					<ul class="left-menu">
						<li class:active={activeItem === 'Home'} on:click={() => handleClick('Home', '/#home')}>
							<a href="/#home">Home</a>
						</li>
						<li class:active={activeItem === 'Services'} on:click={() => handleClick('Services', '/#services')}>
							<a href="/#services">Services</a>
						</li>
						<li class:active={activeItem === 'Containers'} on:click={() => handleClick('Containers', '/#containers')}>
							<a href="/#containers">Containers</a>
						</li>
					</ul>
					<button class="cta"> Contact Us </button>
				</nav>
			{/if}
		{:else}
			<nav class="top-menu" transition:fly={{ y: -50, delay: 0, duration: 500, easing: quintOut }}>
				<ul class="left-menu">
					<li class:active={activeItem === 'Home'} on:click={() => handleClick('Home', '/#home')}>
						<a href="/#home">Home</a>
					</li>
					<li class:active={activeItem === 'Services'} on:click={() => handleClick('Services', '/#services')}>
						<a href="/#services">Services</a>
					</li>
					<li class:active={activeItem === 'Containers'} on:click={() => handleClick('Containers', '/#containers')}>
						<a href="/#containers">Containers</a>
					</li>
				</ul>
				<button class="cta"> Contact Us </button>
			</nav>
		{/if}
	{/if}
</MediaQuery>

<style lang="scss">
	.hero-menu {
		display: flex;
		width: 90%;
		justify-content: space-between;
		left: 50%;
		transform: translateX(-50%);
		position: absolute;
		z-index: 999;
		margin-top: 25px;
		.left-menu {
			display: flex;
			li {
				padding: 16px 36px 16px 24px;
				margin: 0 25px;
				list-style-position: inside;
				border-radius: 12px;
				font-size: var(--fs-500);
				list-style-type: none;
				cursor: pointer;
				a {
					text-decoration: none;
					color: var(--black);
				}
				&.active {
					list-style-type: disc;
					font-weight: 600;
					color: var(--white);
					background-color: var(--black);
					a {
						color: var(--white);
					}
				}
				&:not(.active):hover {
					background-color: var(--black-200);
				}
			}
		}
		.cta {
			background-color: var(--black);
			color: var(--white);
			padding: 16px 36px;
			font-size: 24px;
			border-radius: 12px;
			cursor: pointer;
			font-weight: 600;
			margin: 0 25px;
		}
	}

	.top-menu {
		margin-top: 0;
		top: 0;
		background-color: var(--white);
		padding: 25px;
		border-radius: 0 0 50px 50px;
		width: 90%;
		position: fixed;
		z-index: 999;
		left: 50%;
		transform: translateX(-50%);

		display: flex;
		justify-content: space-between;

		.left-menu {
			display: flex;
			li {
				padding: 16px 36px 16px 24px;
				margin: 0 25px;
				list-style-position: inside;
				border-radius: 12px;
				font-size: 24px;
				list-style-type: none;
				cursor: pointer;
				a {
					text-decoration: none;
					color: var(--black);
				}
				&.active {
					list-style-type: disc;
					font-weight: 600;
					color: var(--white);
					background-color: var(--black);
					a {
						color: var(--white);
					}
				}
				&:not(.active):hover {
					background-color: var(--black-200);
				}
			}
		}
		.cta {
			background-color: var(--black);
			color: var(--white);
			padding: 16px 36px;
			font-size: 24px;
			border-radius: 12px;
			cursor: pointer;
			font-weight: 600;
			margin: 0 25px;
		}
	}
</style>
