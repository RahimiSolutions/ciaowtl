<script>
	import cornerNotch from '$lib/images/corner-notch.svg';
	export let title = '';
	export let text = '';
	export let imageUrl = '';
</script>

<div class="card">
	<div class="background" style="background-image: url({imageUrl});"></div>
	<div class="overlay"></div>
	<div class="gradient-overlay"></div>
	<div class="top">
		<img loading="lazy" src={cornerNotch} alt="corner notch top left" />
		<h2>{@html title}</h2>
	</div>
	<div class="content">
		<div class="text">{@html text}</div>
	</div>
</div>

<style lang="scss">
	.card {
		width: clamp(15.625rem, 4.9107rem + 16.7411vw, 25rem);
		height: clamp(18.75rem, 11.6071rem + 11.1607vw, 25rem);
		border-radius: 25px;
		overflow: hidden;
		position: relative;
		display: flex;
		flex-direction: column;
		justify-content: flex-end;

		.background {
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			background-size: cover;
			background-position: center;
			z-index: 1;
		}

		.overlay {
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			background-color: rgba(19, 35, 32, 0.3);
			z-index: 2;
		}
		.gradient-overlay {
			position: absolute;
			bottom: 0;
			left: 0;
			width: 100%;
			height: 60%;
			background: linear-gradient(to top, var(--green-600), transparent);
			z-index: 2;
		}

		.top {
			z-index: 3;
			img {
				width: clamp(15.625rem, 12.0536rem + 5.5804vw, 18.75rem);
				top: -1px;
				left: -1px;
				position: absolute;
				rotate: 180deg;
			}
			h2 {
				top: 0;
				left: 25%;
				transform: translateX(-25%);
				position: absolute;
				font-size: var(--fs-500);
				margin-bottom: 10px;
			}
		}
		.content {
			position: relative;
			z-index: 3;
			padding: 20px;
			display: flex;
			justify-content: center;
			.text {
				font-size: var(--fs-400);
				color: white;
				text-align: center;
			}
		}
	}
</style>
