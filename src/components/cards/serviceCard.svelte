<script lang="ts">
	import corner from '$lib/images/square-cornernotch-green.svg';
	import Arrow from '$lib/icons/arrow.svelte';

	import airplanePicture from '$lib/images/plane-landing.jpg';
	import truckPicture from '$lib/images/truck.jpg';
	import cargoshipPicture from '$lib/images/cargo-ship.jpg';
	import trainPicture from '$lib/images/rail.jpg';
	import importPicture from '$lib/images/import.jpg';
	import exportPicture from '$lib/images/export.jpg';
	import projectPicture from '$lib/images/projectcargo.jpg';
	import breakbulkPicture from '$lib/images/breakbulk.jpg';

	export let flipped = false;
	let picture = '';
	let text = '';
	export let title;

	if (title === 'Truck') {
		picture = truckPicture;
		title = 'Truck Freight';
		text =
			'Our reliable trucking services make transporting your goods by road straightforward and stress-free. <br/><br/>Whether you need a full truckload or partial delivery, we ensure safe and timely transport.';
	} else if (title === 'Air') {
		picture = airplanePicture;
		title = 'Air Freight';
		text =
			'Need your shipment to arrive fast? <br/><br/>Our airfreight services are designed for speed and reliability, making sure your time-sensitive cargo reaches its destination on schedule.';
	} else if (title === 'Ship') {
		picture = cargoshipPicture;
		title = 'Seafreight (FCL & LCL)';
		text =
			'Whether it’s a full container load (FCL) or less than container load (LCL), our seafreight services ensure your cargo is handled safely and delivered efficiently, no matter the size.';
	} else if (title === 'Rail') {
		picture = trainPicture;
		title = 'Rail Transport';
		text =
			'Looking for an economical and eco-friendly way to ship your goods? <br/><br/>Our rail transport services offer a cost-effective and sustainable solution for moving freight efficiently.';
	} else if (title === 'Import') {
		picture = importPicture;
		title = 'Import Customs Clearance';
		text =
			'Leave the complexities of import customs to us. <br/><br/>We handle all the paperwork and processes to ensure your goods are cleared and delivered to their destination without delay.';
	} else if (title === 'Export') {
		picture = exportPicture;
		title = 'Export Customs Clearance';
		text =
			'Exporting goods can feel overwhelming, but we simplify the process. <br/><br/>Our expert team manages all customs clearance requirements, ensuring your shipments move smoothly across borders.';
	} else if (title === 'Project') {
		picture = projectPicture;
		title = 'Project Cargo';
		text =
			'Complex shipments, simplified. <br/><br/>Our project cargo service handles the transport of large, heavy, or high-value equipment, tailored to your unique logistics needs—perfect for industrial or specialized projects.';
	} else if (title === 'Breakbulk') {
		picture = breakbulkPicture;
		title = 'Breakbulk Cargo';
		text =
			'Shipping oversized or non-containerized items? <br/><br/>Our breakbulk cargo service specializes in transporting large or heavy items that don’t fit in standard containers, ensuring safe and efficient delivery.';
	}

	function flipCard() {
		flipped = !flipped;
	}
</script>

<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_static_element_interactions -->
<div
	class="card {flipped ? 'flipped' : ''}"
	on:click={() => {
		if (flipped) flipCard();
	}}
>
	<div class="inner">
		<div class="background-image" style="background-image: url({picture});"></div>
		<div class="side front">
			<div class="overlay"></div>
			<div class="title">{title}</div>
			<img src={corner} alt="corner" class="corner" />
			<div class="circle" on:click|stopPropagation={flipCard}>
				<div class="arrow">
					<Arrow width={36} fill="#000" rotation={180} />
				</div>
			</div>
		</div>
		<div class="side back">
			<div>
				<h2>{title}</h2>
				<p>{@html text}</p>
			</div>
		</div>
	</div>
</div>

<style lang="scss">
	.card {
		width: clamp(25rem, 10.7143rem + 22.3214vw, 37.5rem);
		height: 400px;
		border-radius: 25px;
		perspective: 1000px;

		&.flipped .inner {
			transform: rotateY(180deg);
		}

		.background-image {
			position: absolute;
			border-radius: 25px;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			background-size: cover;
			background-position: center;
			z-index: -1;
		}

		.inner {
			position: relative;
			width: 100%;
			height: 100%;
			transition: transform 0.6s;
			transform-style: preserve-3d;
			transform: rotateY(0deg);

			.side {
				position: absolute;
				width: 100%;
				height: 100%;
				backface-visibility: hidden;

				&.front {
					background-size: cover;
					background-position: center;

					.overlay {
						position: absolute;
						top: 0;
						left: 0;
						width: 100%;
						height: 100%;
						background: linear-gradient(to bottom, var(--green-600), transparent);
					}

					.title {
						position: absolute;
						top: 20px;
						left: 50%;
						transform: translateX(-50%);
						color: white;
						font-size: var(--fs-600);
						font-weight: bold;
						text-align: center;
					}

					.corner {
						position: absolute;
						bottom: 0;
						right: 0;
					}

					.circle {
						position: absolute;
						overflow: hidden;
						bottom: 20px;
						right: 20px;
						width: 75px;
						height: 75px;
						background-color: var(--white);
						border-radius: 50%;
						display: flex;
						align-items: center;
						justify-content: center;
						cursor: pointer;
						transition: background-color 0.4s ease;

						.arrow {
							z-index: 99;
							height: 36px;
							width: 36px;
							display: flex;
							align-items: center;
							justify-content: center;
							transition:
								transform 0.6s ease-in-out,
								opacity 0.6s ease-in-out;
						}

						&:hover {
							background-color: var(--green-500);

							.arrow {
								animation: arrowMove 1s ease forwards;
							}
						}

						// Reset animation smoothly when hover is removed
						&:not(:hover) .arrow {
							animation: arrowReturn 0.6s ease forwards;
						}
					}
				}

				&.back {
					background-color: rgba(19, 35, 32, 0.85);
					color: white;
					transform: rotateY(180deg);
					display: flex;
					align-items: center;
					justify-content: center;
					text-align: center;
					padding: 20px;
					cursor: pointer;

					h2 {
						position: absolute;
						top: 20px;
						left: 50%;
						transform: translateX(-50%);
						color: white;
						font-size: var(--fs-600);
						font-weight: bold;
						text-align: center;
					}

					p {
						margin: 0;
						font-size: var(--fs-400);
						line-height: 1.5;
					}
				}
			}
		}
	}
	@keyframes arrowMove {
		0% {
			transform: translateX(0) rotate(0deg);
			opacity: 1;
		}
		50% {
			transform: translateX(75px) rotate(0deg); /* Move to the right */
			opacity: 0;
		}
		51% {
			transform: translate(-50px, 50px) rotate(-45deg); /* Reappear off-screen */
			opacity: 0;
		}
		100% {
			transform: translate(0, 0) rotate(-45deg); /* Slide up to center */
			opacity: 1;
		}
	}

	@keyframes arrowReturn {
		0% {
			transform: translate(0, 0) rotate(-45deg); /* Starting point */
			opacity: 1;
		}
		100% {
			transform: translateX(0) rotate(0deg); /* Return to original */
			opacity: 1;
		}
	}
</style>
