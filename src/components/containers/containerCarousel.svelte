<script>
	import container40 from '$lib/images/container40.svg';
	import container20 from '$lib/images/container20.svg';
	import container10 from '$lib/images/container10.svg';
	import { fly } from 'svelte/transition';
	import { cubicInOut } from 'svelte/easing';
	import { writable } from 'svelte/store';
	import Arrow from '$lib/icons/arrow.svelte';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';

	let containers = [
		{
			title: '10 feet container',
			image: container10,
			metricMeasurments: {
				externalMeasurements: {
					height: '2.59',
					width: '2.44',
					length: '2.99'
				},
				internalMeasurements: {
					height: '2.26',
					width: '2.28',
					length: '2.84'
				},
				doorOpening: {
					height: '2.26',
					width: '2.28'
				}
			},
			impericalMeasurements: {
				externalMeasurements: {
					height: '8.6',
					width: '8',
					length: '9.10'
				},
				internalMeasurements: {
					height: '7.5',
					width: '7.6',
					length: '9.3'
				},
				doorOpening: {
					height: '7.5',
					width: '7.6'
				}
			}
		},
		{
			title: '20 feet container',
			image: container20,
			metricMeasurments: {
				externalMeasurements: {
					height: '2.59',
					width: '2.44',
					length: '6.05'
				},
				internalMeasurements: {
					height: '2.26',
					width: '2.28',
					length: '5.44'
				},
				doorOpening: {
					height: '2.26',
					width: '2.28'
				}
			},
			impericalMeasurements: {
				externalMeasurements: {
					height: '8.6',
					width: '8',
					length: '19.10'
				},
				internalMeasurements: {
					height: '7.5',
					width: '7.6',
					length: '17.10'
				},
				doorOpening: {
					height: '7.5',
					width: '7.6'
				}
			}
		},
		{
			title: '40 feet container',
			image: container40,
			metricMeasurments: {
				externalMeasurements: {
					height: '2.59',
					width: '2.44',
					length: '12.19'
				},
				internalMeasurements: {
					height: '2.26',
					width: '2.28',
					length: '12.04'
				},
				doorOpening: {
					height: '2.26',
					width: '2.28'
				}
			},
			impericalMeasurements: {
				externalMeasurements: {
					height: '8.6',
					width: '8',
					length: '40'
				},
				internalMeasurements: {
					height: '7.5',
					width: '7.6',
					length: '39.6'
				},
				doorOpening: {
					height: '7.5',
					width: '7.6'
				}
			}
		}
	];

	let currentIndex = 0;
	let useMetric = writable(true);

	function nextContainer() {
		currentIndex = (currentIndex + 1) % containers.length;
	}

	function prevContainer() {
		currentIndex = (currentIndex - 1 + containers.length) % containers.length;
	}
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<div class="carousel">
			<div class="header">
				<button on:click={prevContainer}>
					<Arrow />
				</button>
				<h2>{containers[currentIndex].title}</h2>
				<button on:click={nextContainer}>
					<Arrow rotation={180} />
				</button>
			</div>
			<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_static_element_interactions -->
			<div class="toggle" on:click={() => ($useMetric = !$useMetric)}>
				<div class="toggle-option {$useMetric ? 'metric-active' : 'imperial-active'}"></div>
				<div class="toggle-label {$useMetric ? 'active' : 'inactive'}">Metric</div>
				<div class="toggle-label {!$useMetric ? 'active' : 'inactive'}">Imperial</div>
			</div>
			{#key containers[currentIndex]}
				<div class="wrapper">
					<div class="content" in:fly={{ x: 70, duration: 400, delay: 0, easing: cubicInOut }}>
						<div class="image">
							<img
								src={containers[currentIndex].image}
								alt={containers[currentIndex].title}
								width="475"
							/>
						</div>
						<div class="measurements">
							{#if $useMetric}
								<div class="external">
									<div class="title">
										<h3>External Measurements:</h3>
										<ul>
											<li>
												<p>
													Height: <span class="bold"
														>{containers[currentIndex].metricMeasurments.externalMeasurements
															.height}m
													</span>
												</p>
											</li>
											<li>
												<p>
													Width: <span class="bold"
														>{containers[currentIndex].metricMeasurments.externalMeasurements
															.width}m
													</span>
												</p>
											</li>
											<li>
												<p>
													Length: <span class="bold">
														{containers[currentIndex].metricMeasurments.externalMeasurements
															.length}m</span
													>
												</p>
											</li>
										</ul>
									</div>
								</div>
								<div class="internal">
									<div class="title">
										<h3>Internal Measurements:</h3>
										<ul>
											<li>
												<p>
													Height: <span class="bold"
														>{containers[currentIndex].metricMeasurments.internalMeasurements
															.height}m
													</span>
												</p>
											</li>
											<li>
												<p>
													Width: <span class="bold"
														>{containers[currentIndex].metricMeasurments.internalMeasurements
															.width}m
													</span>
												</p>
											</li>
											<li>
												<p>
													Length: <span class="bold">
														{containers[currentIndex].metricMeasurments.internalMeasurements
															.length}m</span
													>
												</p>
											</li>
										</ul>
									</div>
								</div>
								<div class="door">
									<div class="title">
										<h3>Door Opening:</h3>
										<ul>
											<li>
												<p>
													Height: <span class="bold"
														>{containers[currentIndex].metricMeasurments.doorOpening.height}m
													</span>
												</p>
											</li>
											<li>
												<p>
													Width: <span class="bold">
														{containers[currentIndex].metricMeasurments.doorOpening.width}m</span
													>
												</p>
											</li>
										</ul>
									</div>
								</div>
							{:else}
								<div class="external">
									<div class="title">
										<h3>External Measurements:</h3>
										<ul>
											<li>
												<p>
													Height: <span class="bold">
														{containers[currentIndex].impericalMeasurements.externalMeasurements
															.height}
														ft</span
													>
												</p>
											</li>
											<li>
												<p>
													Width:<span class="bold"
														>{containers[currentIndex].impericalMeasurements.externalMeasurements
															.width} ft
													</span>
												</p>
											</li>
											<li>
												<p>
													Length:<span class="bold"
														>{containers[currentIndex].impericalMeasurements.externalMeasurements
															.length}
														ft
													</span>
												</p>
											</li>
										</ul>
									</div>
								</div>
								<div class="internal">
									<div class="title">
										<h3>Internal Measurements:</h3>
										<ul>
											<li>
												<p>
													Height: <span class="bold"
														>{containers[currentIndex].impericalMeasurements.internalMeasurements
															.height} ft
													</span>
												</p>
											</li>
											<li>
												<p>
													Width:<span class="bold"
														>{containers[currentIndex].impericalMeasurements.internalMeasurements
															.width} ft
													</span>
												</p>
											</li>
											<li>
												<p>
													Length: <span class="bold">
														{containers[currentIndex].impericalMeasurements.internalMeasurements
															.length} ft</span
													>
												</p>
											</li>
										</ul>
									</div>
								</div>
								<div class="door">
									<div class="title">
										<h3>Door Opening:</h3>
										<ul>
											<li>
												<p>
													Height: <span class="bold"
														>{containers[currentIndex].impericalMeasurements.doorOpening.height} ft
													</span>
												</p>
											</li>
											<li>
												<p>
													Width: <span class="bold"
														>{containers[currentIndex].impericalMeasurements.doorOpening.width} ft
													</span>
												</p>
											</li>
										</ul>
									</div>
								</div>
							{/if}
						</div>
					</div>
				</div>
			{/key}
		</div>
	{/if}
</MediaQuery>
<MediaQuery query="(max-width: 1023px)" let:matches>
	{#if matches}
		<div class="mobile-carousel">
			<div class="header">
				<button on:click={prevContainer}>
					<Arrow width={32}/>
				</button>
				<h2>{containers[currentIndex].title}</h2>
				<button on:click={nextContainer}>
					<Arrow width={32} rotation={180} />
				</button>
			</div>
			<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_static_element_interactions -->
			<div class="toggle" on:click={() => ($useMetric = !$useMetric)}>
				<div class="toggle-option {$useMetric ? 'metric-active' : 'imperial-active'}"></div>
				<div class="toggle-label {$useMetric ? 'active' : 'inactive'}">Metric</div>
				<div class="toggle-label {!$useMetric ? 'active' : 'inactive'}">Imperial</div>
			</div>
			{#key containers[currentIndex]}
				<div class="wrapper">
					<div class="content" in:fly={{ x: 70, duration: 400, delay: 0, easing: cubicInOut }}>
						<div class="image">
							<img
								src={containers[currentIndex].image}
								alt={containers[currentIndex].title}
								width="300"
							/>
						</div>
					</div>
				</div>
				<div class="measurements">
					{#if $useMetric}
						<div class="external">
							<div class="title">
								<h3>External:</h3>
								<ul>
									<li>
										<p>
											Height: <span class="bold"
												>{containers[currentIndex].metricMeasurments.externalMeasurements.height}m
											</span>
										</p>
									</li>
									<li>
										<p>
											Width: <span class="bold"
												>{containers[currentIndex].metricMeasurments.externalMeasurements.width}m
											</span>
										</p>
									</li>
									<li>
										<p>
											Length: <span class="bold">
												{containers[currentIndex].metricMeasurments.externalMeasurements
													.length}m</span
											>
										</p>
									</li>
								</ul>
							</div>
						</div>
						<div class="internal">
							<div class="title">
								<h3>Internal:</h3>
								<ul>
									<li>
										<p>
											Height: <span class="bold"
												>{containers[currentIndex].metricMeasurments.internalMeasurements.height}m
											</span>
										</p>
									</li>
									<li>
										<p>
											Width: <span class="bold"
												>{containers[currentIndex].metricMeasurments.internalMeasurements.width}m
											</span>
										</p>
									</li>
									<li>
										<p>
											Length: <span class="bold">
												{containers[currentIndex].metricMeasurments.internalMeasurements
													.length}m</span
											>
										</p>
									</li>
								</ul>
							</div>
						</div>
						<div class="door">
							<div class="title">
								<h3>Door Opening:</h3>
								<ul>
									<li>
										<p>
											Height: <span class="bold"
												>{containers[currentIndex].metricMeasurments.doorOpening.height}m
											</span>
										</p>
									</li>
									<li>
										<p>
											Width: <span class="bold">
												{containers[currentIndex].metricMeasurments.doorOpening.width}m</span
											>
										</p>
									</li>
								</ul>
							</div>
						</div>
					{:else}
						<div class="external">
							<div class="title">
								<h3>External:</h3>
								<ul>
									<li>
										<p>
											Height: <span class="bold">
												{containers[currentIndex].impericalMeasurements.externalMeasurements.height}
												ft</span
											>
										</p>
									</li>
									<li>
										<p>
											Width:<span class="bold"
												>{containers[currentIndex].impericalMeasurements.externalMeasurements.width}
												ft
											</span>
										</p>
									</li>
									<li>
										<p>
											Length:<span class="bold"
												>{containers[currentIndex].impericalMeasurements.externalMeasurements
													.length}
												ft
											</span>
										</p>
									</li>
								</ul>
							</div>
						</div>
						<div class="internal">
							<div class="title">
								<h3>Internal:</h3>
								<ul>
									<li>
										<p>
											Height: <span class="bold"
												>{containers[currentIndex].impericalMeasurements.internalMeasurements
													.height} ft
											</span>
										</p>
									</li>
									<li>
										<p>
											Width:<span class="bold"
												>{containers[currentIndex].impericalMeasurements.internalMeasurements.width}
												ft
											</span>
										</p>
									</li>
									<li>
										<p>
											Length: <span class="bold">
												{containers[currentIndex].impericalMeasurements.internalMeasurements.length}
												ft</span
											>
										</p>
									</li>
								</ul>
							</div>
						</div>
						<div class="door">
							<div class="title">
								<h3>Door Opening:</h3>
								<ul>
									<li>
										<p>
											Height: <span class="bold"
												>{containers[currentIndex].impericalMeasurements.doorOpening.height} ft
											</span>
										</p>
									</li>
									<li>
										<p>
											Width: <span class="bold"
												>{containers[currentIndex].impericalMeasurements.doorOpening.width} ft
											</span>
										</p>
									</li>
								</ul>
							</div>
						</div>
					{/if}
				</div>
			{/key}
		</div>
	{/if}
</MediaQuery>

<style lang="scss">
	.carousel {
		margin: 150px auto 100px auto;
		display: flex;
		flex-direction: column;
		align-items: center;

		.header {
			display: flex;
			align-items: center;

			h2 {
				margin: 0 1rem;
				font-size: var(--fs-600);
				font-weight: 900;
				color: var(--green-500);
			}

			button {
				background: none;
				border: none;
				font-size: 1.5rem;
				cursor: pointer;
				display: flex;
				justify-content: center;
			}
		}

		.toggle {
			margin: 1rem 0;
			display: inline-flex;
			align-items: center;
			border: 0.5px solid var(--blue-200);
			border-radius: 25px;
			background-color: var(--white);
			overflow: hidden;
			position: relative;
			width: 200px;
			height: 40px;
			cursor: pointer;
			user-select: none;

			.toggle-label {
				flex: 1;
				text-align: center;
				font-size: var(--fs-400);
				color: black;
				z-index: 2;

				&.active {
					color: var(--white);
					font-weight: bold;
				}

				&.inactive {
					color: var(--black);
				}
			}

			.toggle-option {
				position: absolute;
				top: 0;
				left: 0;
				width: 50%;
				height: 100%;
				background-color: var(--green-500);
				border-radius: 25px;
				transition:
					transform 0.3s ease,
					color 0.3s ease;
				z-index: 1;

				&.metric-active {
					transform: translateX(0%);
				}

				&.imperial-active {
					transform: translateX(100%);
				}
			}
		}

		.wrapper {
			min-height: 550px;
		}
		.content {
			position: relative;
			.image {
				margin: 1rem 0;

				img {
					max-width: 100%;
					height: auto;
				}
			}

			.measurements {
				.external,
				.internal,
				.door {
					position: absolute;
					background-color: var(--green-200);
					backdrop-filter: blur(4px);
					border-radius: 15px;
					padding: 20px;
					.title {
						font-size: var(--fs-500);
						color: var(--green-500);
					}
					ul {
						li {
							list-style-type: none;
							p {
								font-size: var(--fs-400);
								color: var(--black);
								line-height: 150%;
								.bold {
									font-weight: 800;
								}
							}
						}
					}
				}

				.external {
					top: 5%;
					left: -60%;
				}
				.internal {
					top: 80%;
					left: -25%;
				}
				.door {
					top: 50%;
					right: -35%;
				}
			}
		}
	}
	.mobile-carousel {
		margin: 150px auto 50px auto;
		display: flex;
		flex-direction: column;
		align-items: center;
		position: relative;
		width: 100%;
		overflow-x: hidden;

		.header {
			display: flex;
			align-items: center;

			h2 {
				margin: 0 1rem;
				font-size: var(--fs-600);
				font-weight: 900;
				color: var(--green-500);
			}

			button {
				background: none;
				border: none;
				font-size: 1.5rem;
				cursor: pointer;
				display: flex;
				justify-content: center;
			}
		}

		.toggle {
			margin: 1rem 0;
			display: inline-flex;
			align-items: center;
			border: 0.5px solid var(--blue-200);
			border-radius: 25px;
			background-color: var(--white);
			overflow: hidden;
			position: relative;
			width: 200px;
			height: 40px;
			cursor: pointer;
			user-select: none;

			.toggle-label {
				flex: 1;
				text-align: center;
				font-size: var(--fs-400);
				color: black;
				z-index: 2;

				&.active {
					color: var(--white);
					font-weight: bold;
				}

				&.inactive {
					color: var(--black);
				}
			}

			.toggle-option {
				position: absolute;
				top: 0;
				left: 0;
				width: 50%;
				height: 100%;
				background-color: var(--green-500);
				border-radius: 25px;
				transition:
					transform 0.3s ease,
					color 0.3s ease;
				z-index: 1;

				&.metric-active {
					transform: translateX(0%);
				}

				&.imperial-active {
					transform: translateX(100%);
				}
			}
		}

		.wrapper {
			min-height: 400px;
		}
		.content {
			.image {
				margin: 1rem 0;

				img {
					max-width: 100%;
					height: auto;
				}
			}
		}
		.measurements {
			position: absolute;
			top: 25%;
			left: 0;
			padding: 8px;
			background-color: var(--green-200);
			backdrop-filter: blur(4px);
			border-radius: 0 16px 16px 0;
			padding: 20px;

			.external,
			.internal,
			.door {
				margin-bottom: 24px;
				.title {
					font-size: var(--mfs-500);
					color: var(--green-500);
				}
				ul {
					li {
						list-style-type: none;
						p {
							font-size: var(--mfs-400);
							color: var(--black);
							line-height: 150%;
							.bold {
								font-weight: 800;
							}
						}
					}
				}
			}
		}
	}
</style>
