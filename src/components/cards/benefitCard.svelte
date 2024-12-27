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
		<div class="text">{text}</div>
	</div>
</div>

<style lang="scss">
	.card {
		width: 400px;
		height: 450px;
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
				width: 300px;
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
				font-size: var(--fs-500);
				color: white;
				text-align: center;
				width: 20ch;
			}
		}
	}
</style>
