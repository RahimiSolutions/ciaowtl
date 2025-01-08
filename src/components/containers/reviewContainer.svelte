<script>
	import { goto } from '$app/navigation';
	import manOne from '$lib/images/manOne.jpg';
	import manTwo from '$lib/images/manTwo.jpg';
	import womanOne from '$lib/images/womanOne.jpg';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';

	function handleClick() {
		goto('/#reviews');
	}
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_static_element_interactions -->
		<div class="container" onclick={handleClick}>
			<div class="images">
				<div class="image" style="background-image: url({manOne});"></div>
				<div class="image" style="background-image: url({manTwo});"></div>
				<div class="image" style="background-image: url({womanOne});"></div>
			</div>
			<div class="text-container">
				<div class="title">40+ Happy Clients</div>
				<div class="reviews">
					<p>5.0 stars</p>
					<p>Google Reviews</p>
				</div>
			</div>
		</div>
	{/if}
</MediaQuery>
<MediaQuery query="(max-width: 1023px)" let:matches>
	{#if matches}
		<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_static_element_interactions -->
		<div class="mobile-container" onclick={handleClick}>
			<div class="images">
				<div class="image" style="background-image: url({manOne});"></div>
				<div class="image" style="background-image: url({manTwo});"></div>
				<div class="image" style="background-image: url({womanOne});"></div>
			</div>
			<div class="text-container">
				<div class="title">40+ Happy Clients</div>
				<div class="reviews">
					<p>5.0 stars</p>
					<p>Google Reviews</p>
				</div>
			</div>
		</div>
	{/if}
</MediaQuery>

<style lang="scss">
	.container {
		cursor: pointer;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		height: 100px;

		.images {
			position: relative;
			width: 200px; /* Adjust based on the number of images and their overlap */
			height: 100px;

			.image {
				border: 3px solid white;
				border-radius: 50%;
				position: absolute;
				top: 0;
				left: 0;
				width: 100px;
				height: 100px;
				background-size: cover;

				z-index: -1;

				&:nth-child(1) {
					left: 0;
					background-position: center;
				}

				&:nth-child(2) {
					left: 50px;
					background-position: top;
				}

				&:nth-child(3) {
					left: 100px;
					background-position: top;
				}
			}
		}

		.text-container {
			margin-left: 20px;
			display: flex;
			flex-direction: column;
			height: 100%;
			justify-content: space-evenly;

			.title {
				font-weight: 600;
				font-size: var(--fs-500);
			}

			.reviews {
				display: flex;
				gap: 8px;

				p {
					border: 1px solid black;
					border-radius: 5px;
					padding: 4px 12px;
					font-size: var(--fs-400);
				}
			}
		}
	}
	.mobile-container {
		cursor: pointer;
		display: flex;
		gap: 4px;
		flex-direction: column;
		align-items: start;
		width: 100%;

		.images {
			position: relative;
			width: 200px; /* Adjust based on the number of images and their overlap */
			height: clamp(4rem, 3.0677rem + 4.9724vw, 6.25rem);

			.image {
				border: 3px solid white;
				border-radius: 50%;
				position: absolute;
				top: 0;
				left: 0;
				width: clamp(4rem, 3.0677rem + 4.9724vw, 6.25rem);
				height: clamp(4rem, 3.0677rem + 4.9724vw, 6.25rem);
				background-size: cover;

				z-index: -1;

				&:nth-child(1) {
					left: 0;
					background-position: center;
				}

				&:nth-child(2) {
					left: 50px;
					background-position: top;
				}

				&:nth-child(3) {
					left: 100px;
					background-position: top;
				}
			}
		}

		.text-container {
			margin-left: 4px;
			display: flex;
			flex-direction: column;
			height: 100%;
			justify-content: space-evenly;

			.title {
				font-weight: 600;
				font-size: var(--mfs-600);
			}

			.reviews {
				display: flex;
				gap: 8px;

				p {
					border: 1px solid black;
					border-radius: 5px;
					padding: 4px 12px;
					font-size: var(--mfs-500);
				}
			}
		}
	}
</style>
