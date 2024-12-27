<script>
	import airplane from '$lib/icons/airplane.svg';
	import truck from '$lib/icons/truck.svg';
	import ship from '$lib/icons/ship.svg';
	import train from '$lib/icons/train.svg';
	import importIcon from '$lib/icons/import.svg';
	import exportIcon from '$lib/icons/export.svg';
	import projectIcon from '$lib/icons/project.svg';
	import breakbulkIcon from '$lib/icons/breakbulk.svg';

	import airplanePicture from '$lib/images/plane-landing.jpg';
	import truckPicture from '$lib/images/truck.jpg';
	import cargoshipPicture from '$lib/images/cargo-ship.jpg';
	import trainPicture from '$lib/images/rail.jpg';
	import importPicture from '$lib/images/import.jpg';
	import exportPicture from '$lib/images/export.jpg';
	import projectPicture from '$lib/images/projectcargo.jpg';
	import breakbulkPicture from '$lib/images/breakbulk.jpg';


	export let number;
	export let text;

    let picture="";
	let icon = '';

	if (text === 'Truck') {
		icon = truck;
        picture = truckPicture;
	} else if (text === 'Air') {
		icon = airplane;
        picture = airplanePicture;
	} else if (text === 'Ship') {
		icon = ship;
        picture = cargoshipPicture;
	} else if (text === 'Rail') {
		icon = train;
		picture = trainPicture;
	} else if (text === 'Import') {
		icon = importIcon;
		picture = importPicture;
	} else if (text === 'Export') {
		icon = exportIcon;
		picture = exportPicture;
	} else if (text === 'Project') {
		icon = projectIcon;
		picture = projectPicture;
	} else if (text === 'Breakbulk') {
		icon = breakbulkIcon;
		picture = breakbulkPicture;
	}
</script>

<div class="card">
	<div class="background" style="background-image: url({picture});"></div>
	<div class="icon">
		<img loading="lazy" src={icon} alt="icon" />
	</div>
	<div class="number">{number}</div>
	<div class="text">{text}</div>
</div>

<style>
	.card {
		position: relative;
		width: 400px;
		height: 300px;
		border-radius: 25px;
		overflow: hidden;
		color: white;
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
		text-align: center;
		cursor: pointer;
	}
	

	.background {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-size: cover;
		background-position: center;
		z-index: -1;
	}

	.icon {
		position: absolute;
		top: 10px;
		left: 10px;
		width: 50px;
		height: 50px;
		border: 3px solid white;
		border-radius: 50%;
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: transparent;
	}

	.number {
		position: absolute;
		bottom: 10px;
		left: 10px;
		font-size: var(--fs-500);
	}

	.text {
		position: absolute;
		bottom: 10px;
		right: 10px;
		font-size: var(--fs-500);
	}
</style>
