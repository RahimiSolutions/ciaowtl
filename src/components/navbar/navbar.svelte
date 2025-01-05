<script lang="ts">
	import { quintOut } from 'svelte/easing';
	import { fly } from 'svelte/transition';
	import { onMount } from 'svelte';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';
	import { goto } from '$app/navigation';
	import Burgermenu from '../buttons/burgermenu.svelte';

	let showTopMenu: boolean;
	let activeItem = 'Home';
	let navigationOn = false;
	let isMenuOpen = false;
	let closed = true;

	function handleMobileMenuClick() {
		closed = !isMenuOpen;
		console.log(closed ? 'closed' : 'open');
	}

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
		closed = true;
		isMenuOpen = false;
		goto(link);
	}

	onMount(() => {
		window.addEventListener('scroll', handleScroll, { passive: true });

		setTimeout(() => {
			navigationOn = true;
		}, 200); // Adjust delay as needed
	});
</script>

<MediaQuery query="(max-width: 1799px)" let:matches>
	{#if matches}
		<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_noninteractive_element_interactions -->
		{#if !showTopMenu}
			{#if navigationOn}
				<nav
					class="hero-menu-1024"
					transition:fly={{ y: -50, delay: 300, duration: 600, easing: quintOut }}
				>
					<div class="dropdown">
						<div class="dropdown-closed">
							<input
								type="checkbox"
								id="checkbox"
								bind:checked={isMenuOpen}
								on:change={handleMobileMenuClick}
							/>
							<label for="checkbox" class="toggle">
								<div class="bar bar--top"></div>
								<div class="bar bar--middle"></div>
								<div class="bar bar--bottom"></div>
							</label>
						</div>
						{#if !closed}
							<ul class="dropdown-opened">
								<li
									class:active={activeItem === 'Home'}
									on:click={() => handleClick('Home', '/#home')}
								>
									<a href="/#home">Home</a>
								</li>
								<li
									class:active={activeItem === 'Services'}
									on:click={() => handleClick('Services', '/#services')}
								>
									<a href="/#services">Services</a>
								</li>
								<li
									class:active={activeItem === 'Containers'}
									on:click={() => handleClick('Containers', '/#containers')}
								>
									<a href="/#containers">Containers</a>
								</li>
							</ul>
						{/if}
					</div>

					<button class="cta" on:click={() => handleClick('', '/#contact')}>
						<a href="/#contact">Contact Us</a>
					</button>
				</nav>
			{/if}
		{:else}
			<nav class="top-menu" transition:fly={{ y: -50, delay: 0, duration: 500, easing: quintOut }}>
				<ul class="left-menu">
					<li class:active={activeItem === 'Home'} on:click={() => handleClick('Home', '/#home')}>
						<a href="/#home">Home</a>
					</li>
					<li
						class:active={activeItem === 'Services'}
						on:click={() => handleClick('Services', '/#services')}
					>
						<a href="/#services">Services</a>
					</li>
					<li
						class:active={activeItem === 'Containers'}
						on:click={() => handleClick('Containers', '/#containers')}
					>
						<a href="/#containers">Containers</a>
					</li>
				</ul>
				<button class="cta" on:click={() => handleClick('', '/#contact')}>
					<a href="/#contact">Contact Us</a></button>
			</nav>
		{/if}
	{/if}
</MediaQuery>
<MediaQuery query="(min-width: 1800px)" let:matches>
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
						<li
							class:active={activeItem === 'Services'}
							on:click={() => handleClick('Services', '/#services')}
						>
							<a href="/#services">Services</a>
						</li>
						<li
							class:active={activeItem === 'Containers'}
							on:click={() => handleClick('Containers', '/#containers')}
						>
							<a href="/#containers">Containers</a>
						</li>
					</ul>
					<button class="cta" on:click={() => handleClick('', '/#contact')}>
						<a href="/#contact">Contact Us</a>
					</button>
				</nav>
			{/if}
		{:else}
			<nav class="top-menu" transition:fly={{ y: -50, delay: 0, duration: 500, easing: quintOut }}>
				<ul class="left-menu">
					<li class:active={activeItem === 'Home'} on:click={() => handleClick('Home', '/#home')}>
						<a href="/#home">Home</a>
					</li>
					<li
						class:active={activeItem === 'Services'}
						on:click={() => handleClick('Services', '/#services')}
					>
						<a href="/#services">Services</a>
					</li>
					<li
						class:active={activeItem === 'Containers'}
						on:click={() => handleClick('Containers', '/#containers')}
					>
						<a href="/#containers">Containers</a>
					</li>
				</ul>
				<button class="cta" on:click={() => handleClick('', '/#contact')}>
					<a href="/#contact">
						Contact Us
					</a>
				</button>
			</nav>
		{/if}
	{/if}
</MediaQuery>

<style lang="scss">
	.hero-menu {
		display: flex;
		width: 90%;
		max-width: 2150px;
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
				margin: 0 24px;
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
			margin: 0 24px;
			a {
				text-decoration: none;
				color: var(--white);
			}
		}
	}
	.hero-menu-1024 {
		display: flex;
		width: 90%;
		height: 75px;
		align-items: center;
		justify-content: space-between;
		left: 50%;
		transform: translateX(-50%);
		position: absolute;
		z-index: 999;
		margin-top: 25px;

		.dropdown {
			position: relative;
			width: 200px;
			margin: 0 24px;

			display: flex;
			justify-content: start;

			.dropdown-closed {
				width: 100%;
				background-color: var(--black);
				padding: 16px 36px;
				border-radius: 12px;
				#checkbox {
					display: none;
				}

				.toggle {
					position: relative;
					width: 40px;
					cursor: pointer;
					margin: auto;
					display: block;
					height: calc(4px * 3 + 11px * 2);

					.bar {
						position: absolute;
						left: 0;
						right: 0;
						height: 3px;
						border-radius: calc(4px / 2);
						background: var(--white);
						color: inherit;
						opacity: 1;
						transition: none 0.35s cubic-bezier(0.5, -0.35, 0.35, 1.5) 0s;

						&--top {
							bottom: calc(50% + 11px + 4px / 2);
							transition-property: bottom, transform;
							transition-delay: calc(0s + 0.35s), 0s;
						}

						&--middle {
							top: calc(50% - 4px / 2);
							transition-property: opacity;
							transition-delay: calc(0s + 0.35s);
						}

						&--bottom {
							top: calc(50% + 11px + 4px / 2);
							transition-property: top, transform;
							transition-delay: calc(0s + 0.35s), 0s;
						}
					}
				}

				#checkbox:checked + .toggle {
					.bar {
						&--top {
							bottom: calc(50% - 4px / 2);
							transform: rotate(135deg);
							transition-delay: 0s, calc(0s + 0.35s);
						}

						&--middle {
							opacity: 0;
							transition-duration: 0s;
							transition-delay: calc(0s + 0.35s);
						}

						&--bottom {
							top: calc(50% - 4px / 2);
							transform: rotate(225deg);
							transition-delay: 0s, calc(0s + 0.35s);
						}
					}
				}
			}
			.dropdown-opened {
				display: flex;
				flex-direction: column;
				position: absolute;
				background-color: var(--white);
				border-radius: 12px;
				top: 72px;
				left: 0px;
				li {
					padding: 16px 36px 16px 24px;
					margin: 0;
					list-style-position: inside;
					border-radius: 12px;
					font-size: var(--fs-500);
					list-style-type: none;
					width: 200px;
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
		}

		.cta {
			background-color: var(--black);
			color: var(--white);
			padding: 16px 36px;
			font-size: 24px;
			border-radius: 12px;
			cursor: pointer;
			font-weight: 600;
			margin: 0 24px;
			height: 64px;
			width: 200px;
			a {
				text-decoration: none;
				color: var(--white);
			}
		}
	}
	.top-menu {
		margin-top: 0;
		top: 0;
		background-color: var(--white);
		padding: 24px;
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
				margin: 0 24px;
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
			margin: 0 24px;
			a {
				text-decoration: none;
				color: var(--white);
			}
		}
	}
</style>
