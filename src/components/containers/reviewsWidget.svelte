<script lang="ts">
	import { onMount } from 'svelte';
	import Arrow from '../../lib/icons/arrow.svelte';

	import star from '$lib/icons/Star.svg';
	import reviwerImage1 from '$lib/images/manOne.jpg';
	import reviwerImage2 from '$lib/images/womanOne.jpg';
	import { fade, fly, slide } from 'svelte/transition';
	import { quintOut } from 'svelte/easing';

	let reviews = [
		{
			stars: 5,
			text: 'Dealing with Ciao was a pleasure from the beginning, as amazing service and limitless commitment were given up front. <br/>Very professional and out of the box mentality. <br/>Thanks for delivering our goods this fast! Respect for the team!',
			image: reviwerImage1,
			name: 'Majd Aldin Abdelhafiz'
		},
		{
			stars: 5,
			text: 'Schnelles Abwicklung und beste Beratung.',
			image: reviwerImage2,
			name: 'Samira Bagheri'
		}
		// Add more reviews as needed
	];

	let currentIndex = 0;
	let interval: string | number | NodeJS.Timeout | undefined;

	const startCarousel = () => {
		interval = setInterval(() => {
			currentIndex = (currentIndex + 1) % reviews.length;
		}, 6000);
	};

	const stopCarousel = () => {
		clearInterval(interval);
	};

	onMount(() => {
		startCarousel();
		return stopCarousel;
	});

	const nextReview = () => {
		currentIndex = (currentIndex + 1) % reviews.length;
	};

	const prevReview = () => {
		currentIndex = (currentIndex - 1 + reviews.length) % reviews.length;
	};
</script>

<!-- svelte-ignore a11y_no_static_element_interactions -->
<div class="carousel" on:mouseenter={stopCarousel} on:mouseleave={startCarousel}>
	<div class="review-box">
		{#each reviews as review, index}
			<div
				class="review-content"
				style="transform: translateX({(index - currentIndex) * 100}%);"
				in:fade={{ duration: 300 }}
			>
				<div class="stars">
					{#each Array(review.stars) as _}
						<img src={star} alt="Star" class="star-icon" />
					{/each}
				</div>
				<div class="review-text"><p>{@html review.text}</p></div>
				<img class="reviewer-image" src={review.image} alt="Reviewer" />
				<div class="reviewer-name"><p>{review.name}</p></div>
			</div>
		{/each}
	</div>

	<div class="controls">
		<Arrow onClick={prevReview} />
		<Arrow onClick={nextReview} />
	</div>
	<div class="dots">
		{#each reviews as _, index}
			<div class="dot {index === currentIndex ? 'active' : ''}"></div>
		{/each}
	</div>
</div>

<style lang="scss">
	.carousel {
		background-color: var(--green-500);
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		position: relative;
		padding: 50px 0;
		margin: 50px 0;

		.review-box {
			background-color: white;
			width: 70%;
			max-width: 1200px;
			border-radius: 25px;
			padding: 50px;
			display: flex;
			flex-direction: column;
			align-items: center;
			text-align: center;
			position: relative;
			overflow: hidden;
            height: 400px;

			.review-content {
				position: absolute;
				width: 100%;
				height: 100%;
                top: 0;
				transition: transform 0.3s ease-out;
				display: flex;
				flex-direction: column;
				justify-content: center;
				align-items: center;
			}

			.stars {
				margin-bottom: 16px;
				img {
					margin: 0 4px;
				}
			}

			.review-text {
				margin-bottom: 24px;
				p {
					width: 60ch;
					font-size: var(--fs-500);
				}
			}

			.reviewer-image {
				width: 100px;
				height: 100px;
				border-radius: 50%;
				margin-bottom: 16px;
				object-fit: cover;
			}

			.reviewer-name {
				p {
					font-weight: 700;
					font-size: var(--fs-400);
				}
			}
		}

		.controls {
			position: absolute;
			display: flex;
			width: 70%;
			max-width: 1200px;
			justify-content: space-between;
			padding: 0 20px;
			cursor: pointer;
		}

		.dots {
			display: flex;
			justify-content: center;
			margin-top: 10px;

			.dot {
				width: 16px;
				height: 16px;
				border-radius: 50%;
				background-color: grey;
				margin: 0 5px;

				&.active {
					background-color: white;
				}
			}
		}
	}
</style>
