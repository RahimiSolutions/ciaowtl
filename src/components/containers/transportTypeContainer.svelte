<script lang="ts">
	import { goto } from '$app/navigation';
	import Arrow from '$lib/icons/arrow.svelte';
	import TransportType from '../cards/transportType.svelte';
	import { writable } from 'svelte/store';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';
	import { Spring } from 'svelte/motion';

	const services = [
		{ number: '01', text: 'Truck' },
		{ number: '02', text: 'Air' },
		{ number: '03', text: 'Ship' },
		{ number: '04', text: 'Rail' },
		{ number: '05', text: 'Import' },
		{ number: '06', text: 'Export' },
		{ number: '07', text: 'Project' },
		{ number: '08', text: 'Breakbulk' }
	];

	function gotoService(service: string) {
		goto(`#${service}`);
	}

	let containerWidth: number;
	let cardWidth: number;
	let position = new Spring(0, { stiffness: 0.9, damping: 0.5 });
	let isDragging = false;
	let startX: number;
	let startPosition: number;
	let currentIndex = 0;
	let velocity = 0;
	let lastX: number;
	let lastTime: number;

	let velocityTracker = { x: 0, t: 0 };

	function updateVelocity(x: number, t: number) {
		const dt = t - velocityTracker.t;
		velocityTracker.x = (x - velocityTracker.x) / dt;
		velocityTracker.t = t;
	}

	function decelerate(timestamp: number) {
		if (!isDragging) {
			const elapsed = timestamp - lastTime;
			velocity *= Math.pow(0.95, elapsed / 16);
			position.target += velocity * elapsed;

			if (Math.abs(velocity) > 0.1) {
				requestAnimationFrame(decelerate);
			} else {
				snapToNearest();
			}
		}
	}

	function snapToNearest() {
		const closestIndex = Math.round(-position.current / (cardWidth + 24));
		position.set(-closestIndex * (cardWidth + 24), { hard: false });
	}

	function next() {
		if (currentIndex < services.length - Math.floor(containerWidth / cardWidth)) {
			currentIndex++;
			position.set(-currentIndex * cardWidth);
		}
	}

	function prev() {
		if (currentIndex > 0) {
			currentIndex--;
			position.set(-currentIndex * cardWidth);
		}
	}

	function handleStart(event: MouseEvent | TouchEvent) {
		isDragging = true;
		startX = event instanceof MouseEvent ? event.clientX : event.touches[0].clientX;
		lastX = startX;
		lastTime = Date.now();
		velocity = 0;
		startPosition = position.current;
		velocityTracker = { x: startX, t: lastTime };
	}

	function handleMove(event: MouseEvent | TouchEvent) {
		if (!isDragging) return;
		const currentX = event instanceof MouseEvent ? event.clientX : event.touches[0].clientX;
		const currentTime = Date.now();

		updateVelocity(currentX, currentTime);

		const dx = currentX - lastX;
		const newPosition = position.current + dx;
		const maxPosition = 0;
		const minPosition = -(services.length - 1) * (cardWidth + 24) - containerWidth;
		position.target = Math.max(minPosition, Math.min(maxPosition, newPosition));

		lastX = currentX;
		lastTime = currentTime;
	}

	function handleEnd() {
		if (!isDragging) return;
		isDragging = false;
		requestAnimationFrame(decelerate);
	}
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<div class="wrapper">
			<div class="container" bind:clientWidth={containerWidth}>
				<!-- svelte-ignore a11y_no_static_element_interactions -->
				<div
					class="card-container"
					on:mousedown={handleStart}
					on:mousemove={handleMove}
					on:mouseup={handleEnd}
					on:mouseleave={handleEnd}
					on:touchstart={handleStart}
					on:touchmove={handleMove}
					on:touchend={handleEnd}
					style="transform: translateX({position.current}px);"
				>
					{#each services as service}
						<!-- svelte-ignore a11y_click_events_have_key_events -->
						<div on:click={() => gotoService(service.text)} bind:clientWidth={cardWidth}>
							<TransportType number={service.number} text={service.text} />
						</div>
					{/each}
				</div>
			</div>
			<div class="arrows">
				<button on:click={prev} disabled={currentIndex === 0}>
					<Arrow width={48} fill="#fff" />
				</button>
				<button
					on:click={next}
					disabled={currentIndex === services.length - Math.floor(containerWidth / cardWidth)}
				>
					<Arrow width={48} fill="#fff" rotation={180} />
				</button>
			</div>
		</div>
	{/if}
</MediaQuery>
<MediaQuery query="(max-width: 1023px)" let:matches>
	{#if matches}
		<div class="mobile-wrapper">
			<div class="container" bind:clientWidth={containerWidth}>
				<!-- svelte-ignore a11y_no_static_element_interactions -->
				<div
					class="card-container"
					on:mousedown={handleStart}
					on:mousemove={handleMove}
					on:mouseup={handleEnd}
					on:mouseleave={handleEnd}
					on:touchstart={handleStart}
					on:touchmove={handleMove}
					on:touchend={handleEnd}
					style="transform: translateX({position.current}px);"
				>
					<!-- svelte-ignore a11y_click_events_have_key_events -->
					{#each services as service}
						<div on:click={() => gotoService(service.text)} bind:clientWidth={cardWidth}>
							<TransportType number={service.number} text={service.text} />
						</div>
					{/each}
				</div>
			</div>
		</div>
	{/if}
</MediaQuery>

<style lang="scss">
	.wrapper {
		position: relative;
		.container {
			width: 100%;
			overflow-x: hidden;
			.card-container {
				display: flex;
				width: fit-content;
				gap: 24px;
				transition: transform 0.3s ease;
				user-select: none;
			}
		}
		.arrows {
			display: flex;
			justify-content: start;
			margin-top: 16px;
			position: absolute;
			top: 100%;
			button {
				margin: 0 8px;
				padding: 4px 8px;
				background-color: var(--green-500);
				color: var(--white);
				border: none;
				border-radius: 4px;
				cursor: pointer;
				font-size: var(--fs-500);
				&:disabled {
					background-color: var(--green-200);
					cursor: not-allowed;
				}
			}
		}
	}
	.mobile-wrapper {
		position: relative;
		.container {
			width: 100%;

			.card-container {
				display: flex;
				width: fit-content;
				gap: 24px;
				transition: transform 0.3s ease;
				user-select: none;
				cursor: grab;
				padding-right: calc(100% - var(--card-visible-width));
			}
		}
	}
</style>
