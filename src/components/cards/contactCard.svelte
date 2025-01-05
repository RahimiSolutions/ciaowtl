<script>
	import squareCorner from '$lib/images/square-cornernotch-white.svg';

	import chatBubbles from '$lib/icons/chatbubbles.svg';
	import phone from '$lib/icons/phone.svg';
	import geo from '$lib/icons/geo.svg';

	let { type } = $props();
	let actionText = '';
	let action = '';
	let title = '';
	let text = '';
	let icon = '';

	if (type === 'email') {
		title = 'Reach Out';
		text = 'We’re here to help';
		actionText = 'info@ciao-wtl.com';
		action = 'mailto:info@ciao-wtl.com';
		icon = chatBubbles;
	} else if (type === 'phone') {
		title = 'Call Us';
		text = 'Mon-Fri from 8am to 5pm';
		actionText = '+49 4075 695565';
		action = 'tel:+494075695565';
		icon = phone;
	} else if (type === 'address') {
		title = 'Visit Us';
		text = 'Visit our offices in Hamburg';
		actionText = 'View on Google Maps';
		action = 'https://maps.app.goo.gl/4e4pP2iXDDNg6Nvb6';
		icon = geo;
	}
</script>

<div class="card">
	<img class="notch" src={squareCorner} alt="Square corner notch scalable vector graphic" />
	<img class="icon" src={icon} alt="icon for contact card" />
	<div class="content">
		<div class="title"><h2>{title}</h2></div>
		<div class="text"><p>{text}</p></div>
		<div class="actionText"><a href={action} target="_blank">{actionText}</a></div>
	</div>
</div>

<style lang="scss">
	.card {
		background-color: var(--green-200);
		width: clamp(18.75rem, 11.6071rem + 11.1607vw, 25rem);

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
