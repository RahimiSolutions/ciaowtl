<script>
	import { goto } from '$app/navigation';

	export let bgColorHover = '#f5f5f5';
	export let text = 'text';
	export let link = '';
	export let borderRadius = '0px';
	export let borderWidth = '0px';

	function goToLink() {
		if (link) {
			if (link.startsWith('http://') || link.startsWith('https://')) {
				// External link: Use window.location for external navigation
				window.location.href = link;
			} else {
				// Internal link: Use SvelteKit's goto function for internal navigation
				goto(link);
			}
		}
	}
</script>

<button
	class="button"
	style:border-radius={borderRadius}
	style:border-width={borderWidth}
	style:border-color={bgColorHover}
	style="--bgColorHover: {bgColorHover};"
	on:click|preventDefault|stopPropagation={goToLink}
>
	{text}
</button>

<style lang="scss">
	button {
		cursor: pointer;
		background-color: var(--green-500);
		color: var(--white);
		font-size: var(--fs-500);

		border-radius: 100vw;
		padding: 16px 24px;
		// box-shadow: 4px 4px 12px 0 rgba(0, 0, 0, 0.25);

		transition: ease-in-out 0.3s;
		// &:hover {
		// 	box-shadow: 8px 8px 24px rgba(219, 34, 34, 0.5);
		// }
	}
</style>
