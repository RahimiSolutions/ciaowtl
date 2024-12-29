<script>
	import { goto } from '$app/navigation';

	let { bgColorHover = '#f5f5f5', text = 'text', link = '', borderRadius = '0px', borderWidth = '0px', onClick} = $props();
	

	function handleClick() {
		if (link) {
			if (link.startsWith('http://') || link.startsWith('https://')) {
				window.location.href = link;
			} else {
				goto(link);
			}
		}
		if (onClick) onClick();
	}
</script>

<button
	class="button"
	style:border-radius={borderRadius}
	style:border-width={borderWidth}
	style:border-color={bgColorHover}
	style="--bgColorHover: {bgColorHover};"
	onclick={handleClick}
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
