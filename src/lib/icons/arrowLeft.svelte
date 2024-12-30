<script>
    let {width = 36, fill = "#000", onClick = () => {}} = $props();

    function handleClick() {
		if (onClick) onClick();
	}
</script>

<svg onclick={handleClick} {width} viewBox="0 0 64 64" fill={fill} xmlns="http://www.w3.org/2000/svg">
<path d="M28 52L8 32M8 32L28 12M8 32H56" stroke={fill} stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
