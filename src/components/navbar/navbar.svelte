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

<MediaQuery query="(max-width:768px)" let:matches>
	{#if matches}
		<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_noninteractive_element_interactions -->
		{#if !showTopMenu}
			{#if navigationOn}
				<nav
					class="hero-menu-mobile"
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
						<a href="/#contact">Contact</a>
					</button>
				</nav>
			{/if}
		{:else}
			<nav
				class="top-menu-mobile"
				transition:fly={{ y: -50, delay: 0, duration: 500, easing: quintOut }}
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
					<a href="/#contact">Contact Us</a></button
				>
			</nav>
		{/if}
	{/if}
</MediaQuery>
<MediaQuery query="(min-width: 769px) and (max-width: 1499px)" let:matches>
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
					<a href="/#contact">Contact Us</a></button
				>
			</nav>
		{/if}
	{/if}
</MediaQuery>
<MediaQuery query="(min-width: 1500px)" let:matches>
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
					<a href="/#contact"> Contact Us </a>
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
				padding: 12px 16px 12px 16px;
				margin: 0 24px;
				list-style-position: inside;
				border-radius: 12px;
				font-size: var(--fs-500);
				list-style-type: none;
				cursor: pointer;
				transition: background-color 0.3s ease-in-out;
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
			padding: 0px 24px;
			font-size: var(--fs-500);
			border-radius: 12px;
			cursor: pointer;
			font-weight: 600;
			margin: 0 24px;
			border: none;
			a {
				text-decoration: none;
				color: var(--white);
			}
		}
	}
	.hero-menu-1024 {
		display: flex;
		width: 90%;
		align-items: center;
		justify-content: space-between;
		left: 50%;
		transform: translateX(-50%);
		position: absolute;
		z-index: 999;
		margin-top: 25px;

		.dropdown {
			position: relative;
			width: 60px;
			height: 48px;
			margin: 0 24px;

			.dropdown-closed {
				width: 100%;
				height: 100%;
				display: flex;
				justify-content: start;
				align-items: center;
				background-color: var(--black);
				border-radius: 12px;
				#checkbox {
					display: none;
				}

				.toggle {
					position: relative;
					width: 32px;
					cursor: pointer;
					margin: auto;
					display: block;
					height: calc(4px * 3 + 6px * 2); // Reduced from 11px to 6px

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
							bottom: calc(50% + 6px + 4px / 2); // Reduced from 11px to 6px
							transition-property: bottom, transform;
							transition-delay: calc(0s + 0.35s), 0s;
						}

						&--middle {
							top: calc(50% - 4px / 2);
							transition-property: opacity;
							transition-delay: calc(0s + 0.35s);
						}

						&--bottom {
							top: calc(50% + 6px + 4px / 2); // Reduced from 11px to 6px
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
				top: 50px;
				left: 0px;
				li {
					padding: 12px 16px 12px 16px;
					margin: 0;
					list-style-position: inside;
					border-radius: 8px;
					font-size: var(--fs-500);
					list-style-type: none;
					width: 160px;
					cursor: pointer;
					transition: background-color 0.3s ease-in-out;
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
			padding: 0px 24px;
			font-size: var(--fs-500);
			border-radius: 12px;
			cursor: pointer;
			font-weight: 600;
			margin: 0 24px;
			height: 48px;
			width: 160px;
			border: none;
			
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
		padding: 16px 12px;
		border-radius: 0 0 50px 50px;
		width: 90%;
		position: fixed;
		z-index: 999;
		left: 50%;
		transform: translateX(-50%);
		box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.4);

		display: flex;
		justify-content: space-between;

		.left-menu {
			display: flex;
			li {
				padding: 12px 16px 12px 16px;
				margin: 0 24px;
				list-style-position: inside;
				border-radius: 12px;
				font-size: var(--fs-500);
				list-style-type: none;
				cursor: pointer;
				transition: background-color 0.3s ease-in-out;
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
			padding: 0px 24px;
			font-size: var(--fs-500);
			border-radius: 12px;
			cursor: pointer;
			font-weight: 600;
			margin: 0 24px;
			border: none;
			a {
				text-decoration: none;
				color: var(--white);
			}
		}
	}
	.hero-menu-mobile {
		display: flex;
		width: 98%;
		align-items: center;
		justify-content: space-between;
		left: 50%;
		top: 0;
		transform: translateX(-50%);
		position: absolute;
		z-index: 999;
		margin-top: 30px;

		.dropdown {
			position: relative;
			width: 48px;
			height: 32px;
			margin: 0 24px;

			.dropdown-closed {
				width: 100%;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				background-color: var(--black);
				border-radius: 8px;

				#checkbox {
					display: none;
				}

				.toggle {
					position: relative;
					width: 24px;
					cursor: pointer;
					margin: auto;
					display: block;
					height: 18px; // Adjusted height

					.bar {
						position: absolute;
						left: 0;
						right: 0;
						height: 2px;
						border-radius: 1px;
						background: var(--white);
						color: inherit;
						opacity: 1;
						transition: none 0.35s cubic-bezier(0.5, -0.35, 0.35, 1.5) 0s;

						&--top {
							top: 0;
							transition-property: top, transform;
							transition-delay: calc(0s + 0.35s), 0s;
						}

						&--middle {
							top: 8px; // Centered
							transition-property: opacity;
							transition-delay: calc(0s + 0.35s);
						}

						&--bottom {
							bottom: 0;
							transition-property: bottom, transform;
							transition-delay: calc(0s + 0.35s), 0s;
						}
					}
				}

				#checkbox:checked + .toggle {
					.bar {
						&--top {
							top: 8px;
							transform: rotate(45deg);
							transition-delay: 0s, calc(0s + 0.35s);
						}

						&--middle {
							opacity: 0;
							transition-duration: 0s;
							transition-delay: calc(0s + 0.35s);
						}

						&--bottom {
							bottom: 8px;
							transform: rotate(-45deg);
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
				top: 50px;
				left: 0px;
				li {
					padding: 12px 16px 12px 16px;
					margin: 0;
					list-style-position: inside;
					border-radius: 8px;
					font-size: var(--mfs-400);
					list-style-type: none;
					width: 160px;
					cursor: pointer;
					transition: background-color 0.3s ease-in-out;
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
			padding: 0px 8px;
			font-size: var(--mfs-400);
			border-radius: 8px;
			cursor: pointer;
			font-weight: 600;
			margin: 0 24px;
			height: 32px;
			border: none;
			a {
				text-decoration: none;
				color: var(--white);
			}
		}
	}
	.top-menu-mobile {
		margin-top: 0;
		top: 0;
		background-color: var(--white);
		padding: 12px 4px;
		border-radius: 0 0 25px 25px;
		width: 94%;
		height: 76px;
		position: fixed;
		z-index: 999;
		left: 50%;
		transform: translateX(-50%);
		box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.4);

		display: flex;
		justify-content: space-between;
		align-items: center;

		.dropdown {
			position: relative;
			width: 48px;
			height: 32px;
			margin: 0 24px;

			.dropdown-closed {
				width: 100%;
				height: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				background-color: var(--black);
				border-radius: 8px;

				#checkbox {
					display: none;
				}

				.toggle {
					position: relative;
					width: 24px;
					cursor: pointer;
					margin: auto;
					display: block;
					height: 18px; // Adjusted height

					.bar {
						position: absolute;
						left: 0;
						right: 0;
						height: 2px;
						border-radius: 1px;
						background: var(--white);
						color: inherit;
						opacity: 1;
						transition: none 0.35s cubic-bezier(0.5, -0.35, 0.35, 1.5) 0s;

						&--top {
							top: 0;
							transition-property: top, transform;
							transition-delay: calc(0s + 0.35s), 0s;
						}

						&--middle {
							top: 8px; // Centered
							transition-property: opacity;
							transition-delay: calc(0s + 0.35s);
						}

						&--bottom {
							bottom: 0;
							transition-property: bottom, transform;
							transition-delay: calc(0s + 0.35s), 0s;
						}
					}
				}

				#checkbox:checked + .toggle {
					.bar {
						&--top {
							top: 8px;
							transform: rotate(45deg);
							transition-delay: 0s, calc(0s + 0.35s);
						}

						&--middle {
							opacity: 0;
							transition-duration: 0s;
							transition-delay: calc(0s + 0.35s);
						}

						&--bottom {
							bottom: 8px;
							transform: rotate(-45deg);
							transition-delay: 0s, calc(0s + 0.35s);
						}
					}
				}
			}
			.dropdown-opened {
				display: flex;
				flex-direction: column;
				position: absolute;
				background-color: var(--black);
				border-radius: 12px;
				top: 50px;
				left: 0px;
				li {
					padding: 12px 16px 12px 16px;
					margin: 0;
					list-style-position: inside;
					border-radius: 8px;
					font-size: var(--mfs-400);
					list-style-type: none;
					width: 160px;
					cursor: pointer;
					transition: background-color 0.3s ease-in-out;
					a {
						text-decoration: none;
						color: var(--white);
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
			padding: 0px 8px;
			font-size: var(--mfs-500);
			border-radius: 8px;
			border: none;
			cursor: pointer;
			font-weight: 600;
			margin: 0 8px;
			height: 32px;
			a {
				text-decoration: none;
				color: var(--white);
			}
		}
	}
</style>
