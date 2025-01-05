<script>
	import container40 from '$lib/images/container40.svg';
	import container20 from '$lib/images/container20.svg';
	import container10 from '$lib/images/container10.svg';
	import { fade, fly } from 'svelte/transition';
	import { cubicOut } from 'svelte/easing';
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
				<div class="content"  >
					<div class="image">
						<img
							src={containers[currentIndex].image}
							alt={containers[currentIndex].title}
							width="600"
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
												{containers[currentIndex].metricMeasurments.externalMeasurements.height}m
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].metricMeasurments.externalMeasurements.width}m
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].metricMeasurments.externalMeasurements.length}m
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
												{containers[currentIndex].metricMeasurments.internalMeasurements.height}m
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].metricMeasurments.internalMeasurements.width}m
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].metricMeasurments.internalMeasurements.length}m
											</p>
										</li>
									</ul>
								</div>
							</div>
							<div class="door">
								<div class="title">
									<h3>Door Opening:</h3>
									<ul>
										<li><p>{containers[currentIndex].metricMeasurments.doorOpening.height}m</p></li>
										<li><p>{containers[currentIndex].metricMeasurments.doorOpening.width}m</p></li>
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
												{containers[currentIndex].impericalMeasurements.externalMeasurements.height}
												ft
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].impericalMeasurements.externalMeasurements.width} ft
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].impericalMeasurements.externalMeasurements.length}
												ft
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
												{containers[currentIndex].impericalMeasurements.internalMeasurements.height}
												ft
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].impericalMeasurements.internalMeasurements.width} ft
											</p>
										</li>
										<li>
											<p>
												{containers[currentIndex].impericalMeasurements.internalMeasurements.length}
												ft
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
											<p>{containers[currentIndex].impericalMeasurements.doorOpening.height} ft</p>
										</li>
										<li>
											<p>{containers[currentIndex].impericalMeasurements.doorOpening.width} ft</p>
										</li>
									</ul>
								</div>
							</div>
						{/if}
					</div>
				</div>
			{/key}
		</div>
	{/if}
</MediaQuery>

<style lang="scss">
	.carousel {
		margin: 150px auto;
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

			input {
				display: none;
			}

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
							}
						}
					}
				}

				.external {
					top: 10%;
					left: -50%;
				}
				.internal {
					top: 80%;
					left: -25%;
				}
				.door {
					top: 50%;
					right: -25%;
				}
			}
		}
	}

    
</style>
