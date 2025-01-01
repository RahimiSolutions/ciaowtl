<script>
	let { width = 36, fill = '#000', onClick = () => {} , rotation = 0} = $props();

	function handleClick() {
		if (onClick) onClick();
	}
</script>

<!-- svelte-ignore a11y_click_events_have_key_events -->
<!-- svelte-ignore a11y_no_static_element_interactions -->
<svg onclick={handleClick} {width} viewBox="0 0 64 64" {fill} xmlns="http://www.w3.org/2000/svg">
	<g transform="rotate({rotation}, 32, 32)">
    <path
      d="M28 52L8 32M8 32L28 12M8 32H56"
      stroke={fill}
      stroke-width="3"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </g>
</svg>
