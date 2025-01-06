<script>
	import squareCorner from '$lib/images/square-cornernotch-white.svg';

	import chatBubbles from '$lib/icons/chatbubbles.svg';
	import phone from '$lib/icons/phone.svg';
	import geo from '$lib/icons/geo.svg';

	let { type } = $props();
	let state = $state({
		actionText: '',
		action: '',
		title: '',
		text: '',
		icon: ''
	});

	if (type === 'email') {
		state.title = 'Reach Out';
		state.text = 'We’re here to help';
		state.actionText = 'info@ciao-wtl.com';
		state.action = 'mailto:info@ciao-wtl.com';
		state.icon = chatBubbles;
	} else if (type === 'phone') {
		state.title = 'Call Us';
		state.text = 'Mon-Fri from 8am to 5pm';
		state.actionText = '+49 4075 695565';
		state.action = 'tel:+494075695565';
		state.icon = phone;
	} else if (type === 'address') {
		state.title = 'Visit Us';
		state.text = 'Visit our offices in Hamburg';
		state.actionText = 'View on Google Maps';
		state.action = 'https://maps.app.goo.gl/4e4pP2iXDDNg6Nvb6';
		state.icon = geo;
	}
</script>

<div class="card">
	<img class="notch" src={squareCorner} alt="Square corner notch scalable vector graphic" />
	<img class="icon" src={state.icon} alt="icon for contact card" />
	<div class="content">
		<div class="title"><h2>{state.title}</h2></div>
		<div class="text"><p>{state.text}</p></div>
		<div class="actionText"><a href={state.action} target="_blank">{state.actionText}</a></div>
	</div>
</div>

<style lang="scss">
	.card {
		background-color: var(--green-200);
		width: clamp(18.75rem, 15.1786rem + 5.5804vw, 21.875rem);

		height: 400px;
		border-radius: 25px;
		position: relative;

		.notch {
			margin-top: -2px;
			margin-left: -2px;
			rotate: 180deg;
		}
		.icon {
			position: absolute;
			left: 5%;
			top: 5%;
		}

		.content {
			padding: 20px;
			color: var(--black);
			.title {
				margin-bottom: 12px;
				h2 {
					font-weight: 800;
					font-size: var(--fs-600);
				}
			}
			.text {
				margin-bottom: 24px;
				p {
					font-size: var(--fs-500);
				}
			}
			.actionText {
				a {
					text-decoration: none;
					color: var(--black);
					cursor: pointer;
					width: fit-content;
					font-size: var(--fs-500);
					font-weight: 600;
					border-bottom: 3px solid var(--black);
					transition: all 0.2s;

					&:hover {
						border-bottom: 3px solid var(--green-500);
						color: var(--green-500);
						transform: translateY(-1px);
					}
				}
			}
		}
	}
</style>
