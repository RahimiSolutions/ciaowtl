<script>
	import notch from '$lib/images/top-notch.svg';
	import logo from '$lib/images/logo.png';
	import backToTop from '$lib/images/ToTopNotch.svg';
	import Arrow from '$lib/icons/arrow.svelte';
	import corner from '$lib/images/corner.svg';

	import email from '$lib/icons/email.svg';
	import call from '$lib/icons/call.svg';
	import facebook from '$lib/icons/facebook.svg';
	import instagram from '$lib/icons/instagram.svg';
	import linkedin from '$lib/icons/linkedin.svg';
	import whatsapp from '$lib/icons/whatsapp.svg';
	import MediaQuery from '../MediaQuery/MediaQuery.svelte';
</script>

<MediaQuery query="(min-width: 1024px)" let:matches>
	{#if matches}
		<footer class="desktop">
			<div class="notch">
				<div class="container">
					<img src={notch} alt="scalable vector graphic of a top notch" />
					<div class="slogan"><p>Time is money, <br /> and we save you both</p></div>
				</div>
			</div>
			<div class="logo">
				<a href="/#top"><img src={logo} alt="logo Ciao World Transport & Logistics" /></a>
			</div>
			<div class="content">
				<div class="left">
					<div class="contact">
						<h2>Contact Us</h2>
						<ul>
							<li><a href="mailto:info@ciao-wtl.com" target="_blank">info@ciao-wtl.com</a></li>
							<li><a href="tel:+494075695565" target="_blank">+49 4075 695565</a></li>
						</ul>
					</div>
					<div class="business-hours">
						<h2>Business Hours</h2>
						<ul>
							<li>Mon - Fri : 8am - 5pm</li>
						</ul>
					</div>
				</div>
				<div class="right">
					<div class="sitemap">
						<ul>
							<li><a href="/#services">Services</a></li>
							<li><a href="/#reviews">Reviews</a></li>
							<li><a href="/#containers">Containers</a></li>
							<li><a href="/#contact">Contact</a></li>
						</ul>
					</div>
					<div class="links">
						<ul>
							<li><a href="https://wa.me/4917657966211" target="_blank">Get a Quote</a></li>
							<li><a href="/imprint">Imprint</a></li>
						</ul>
					</div>
				</div>
			</div>
			<div class="plug">
				<img class="above" src={corner} alt="scalable vector graphic of corner" />
				<p>
					<a href="https://www.rahimisolutions.com/">Website by Rahimi Solutions</a>
				</p>
				<img class="below" src={corner} alt="scalable vector graphic of corner" />
			</div>
			<div class="line"></div>
			<div class="bottom">
				<div class="left">
					<p>Copyright © 2025 Ciao! World Transport & Logistics UG. All Rights Reserved</p>
				</div>
				<div class="right">
					<div class="back-to-top">
						<div class="to-top-notch">
							<img src={backToTop} alt="" />
						</div>
						<div class="content">
							<div class="arrow">
								<Arrow width={36} fill="#000" rotation={90} onClick={() => window.scrollTo(0, 0)} />
							</div>
							<div class="text">
								<p>Back To Top</p>
							</div>
						</div>
					</div>
					<div class="socials">
						<ul>
							<li>
								<a
									href="https://www.facebook.com/profile.php?id=100095520884839&locale=nb_NO"
									target="_blank"><img src={facebook} alt="facebook icon" /></a
								>
							</li>
							<li>
								<a href="https://www.instagram.com/ciao_wtl/" target="_blank"
									><img src={instagram} alt="instagram icon" /></a
								>
							</li>
							<li>
								<a
									href="https://www.linkedin.com/company/ciao-world-transport-logistics/"
									target="_blank"><img src={linkedin} alt="linkedin icon" /></a
								>
							</li>
							<li>
								<a href="https://wa.me/4917657966211?text=Hi%20Ciao-team%2C%20I%20want%20to%20request%20a%20quote%20from%20%5Bcity%2C%20country%5D%20to%20%5Bcity%2C%20country%5D%0ABest%20regards%2C%0A%5BYour%20Name%5D" target="_blank"
									><img src={whatsapp} alt="whatsapp icon" /></a
								>
							</li>
						</ul>
					</div>
				</div>
			</div>
		</footer>
	{/if}
</MediaQuery>
<MediaQuery query="(max-width: 1023px)" let:matches>
	{#if matches}
		<footer class="mobile">
			<div class="notch">
				<div class="container">
					<img src={notch} alt="scalable vector graphic of a top notch" />
					<div class="slogan"><p>Time is money, <br /> and we save you both</p></div>
				</div>
			</div>
			<div class="content">
				<div class="top">
					<div class="contact">
						<h2>Contact Us</h2>
						<p class="subtext">We're here for you - Mon - Fri : 8am - 5pm</p>
						<ul>
							<li>
								<a href="mailto:info@ciao-wtl.com" target="_blank">
									<img src={email} alt="email icon" />
									info@ciao-wtl.com
								</a>
							</li>
							<li>
								<a href="tel:+494075695565" target="_blank">
									<img src={call} alt="phone icon" />
									+49 4075 695565
								</a>
							</li>
						</ul>
					</div>
				</div>
				<div class="down">
					<div class="sitemap">
						<h2>Sitemap</h2>
						<ul>
							<li><a href="/#services">Services</a></li>
							<li><a href="/#contact">Contact</a></li>
							<li><a href="/#reviews">Reviews</a></li>
							<li><a href="https://wa.me/4917657966211?text=Hi%20Ciao-team%2C%20I%20want%20to%20request%20a%20quote%20from%20%5Bcity%2C%20country%5D%20to%20%5Bcity%2C%20country%5D%0ABest%20regards%2C%0A%5BYour%20Name%5D" target="_blank">Get a Quote</a></li>
							<li><a href="/imprint">Imprint</a></li>
						</ul>
					</div>
					<div class="socials">
						<h2>Our Socials</h2>
						<ul>
							<li>
								<a
									href="https://www.facebook.com/profile.php?id=100095520884839&locale=nb_NO"
									target="_blank"
								>
									<img src={facebook} alt="facebook icon" />
									<p>Facebook</p>
								</a>
							</li>
							<li>
								<a href="https://www.instagram.com/ciao_wtl/" target="_blank">
									<img src={instagram} alt="instagram icon" />
									<p>Instagram</p>
								</a>
							</li>
							<li>
								<a
									href="https://www.linkedin.com/company/ciao-world-transport-logistics/"
									target="_blank"
								>
									<img src={linkedin} alt="linkedin icon" />
									<p>Linkedin</p>
								</a>
							</li>
							<li>
								<a href="https://wa.me/4917657966211" target="_blank">
									<img src={whatsapp} alt="whatsapp icon" />
									<p>Whatsapp</p>
								</a>
							</li>
						</ul>
					</div>
				</div>
			</div>
			<div class="bottom">
				<div class="plug">
					<img class="above" src={corner} alt="scalable vector graphic of corner" />
					<p>
						<a href="https://www.rahimisolutions.com/">Website by Rahimi Solutions</a>
					</p>
					<img class="below" src={corner} alt="scalable vector graphic of corner" />
				</div>
				<div class="back-to-top">
					<div class="arrow">
						<Arrow width={36} fill="#000" rotation={90} onClick={() => window.scrollTo(0, 0)} />
					</div>
				</div>
				<div class="end">
					<p>Copyright © 2025 Ciao! World Transport & Logistics UG. All Rights Reserved</p>
				</div>
			</div>
		</footer>
	{/if}
</MediaQuery>

<style lang="scss">
	.desktop {
		border-radius: 50px;
		background-color: var(--green-600);
		color: var(--white);
		width: 98vw;
		margin: 100px auto 2vh auto;
		padding: 20px;
		position: relative;
		.line {
			border-top: 0.5px solid var(--green-200);
			width: 100%;
			margin: 20px 0;
			background-color: transparent;
		}
		.notch {
			position: absolute;
			top: -1px;
			right: 10%;
			.container {
				position: relative;

				img {
					width: clamp(25rem, 0rem + 39.0625vw, 46.875rem);
				}
				.slogan {
					position: absolute;
					top: 25%;
					left: 50%;
					transform: translateX(-50%);
					text-align: center;
					text-transform: uppercase;
					font-weight: 900;
					font-size: var(--fs-slogan);
					width: 100%;
					color: var(--black);
				}
			}
		}
		.logo {
			margin-top: 50px;
			margin-left: 5%;
			img {
				width: 400px;
			}
		}
		.content {
			display: flex;
			margin: 50px 0;
			align-items: baseline;
			justify-content: space-evenly;
			.left {
				width: 40%;
				display: flex;
				flex-direction: column;
				gap: 24px;
				.contact {
					h2 {
						font-size: var(--fs-500);
						margin-bottom: 16px;
					}
					ul {
						margin-left: 24px;
						li {
							font-size: var(--fs-500);
							list-style-type: none;
							margin-bottom: 16px;
						}
					}
				}
				.business-hours {
					h2 {
						font-size: var(--fs-500);
						margin-bottom: 16px;
					}
					ul {
						margin-left: 24px;
						li {
							font-size: var(--fs-500);
							list-style-type: none;
							margin-bottom: 16px;
						}
					}
				}
			}
			.right {
				margin: 50px 0;
				width: 40%;
				display: flex;
				justify-content: space-evenly;
				.sitemap {
					ul {
						margin-left: 24px;
						li {
							font-size: var(--fs-500);
							list-style-type: none;
							margin-bottom: 16px;
						}
					}
				}
				.links {
					ul {
						margin-left: 24px;
						li {
							font-size: var(--fs-500);
							list-style-type: none;
							margin-bottom: 16px;
						}
					}
				}
			}
		}

		.plug {
			position: absolute;
			right: 0;
			bottom: 20%;
			display: flex;
			align-items: end;
			flex-direction: column;
			.above {
				width: 32px;
				margin-bottom: -1px;
				transform: scaleX(-1);
			}
			.below {
				margin-top: -1px;
				rotate: 180deg;
				width: 32px;
			}
			p {
				width: fit-content;
				background-color: var(--white);
				padding: 4px 16px;
				border-radius: 16px 0px 0px 16px;
				a {
					font-size: var(--fs-500);
					color: var(--black);
				}
			}
		}

		a {
			color: var(--white);
			text-decoration: none;
		}
		.bottom {
			display: flex;
			position: relative;
			height: 98px;
			.left {
				width: 100%;
				display: flex;
				align-items: center;
				p {
					opacity: 0.6;
					font-size: var(--fs-400);
				}
			}
			.right {
				width: 100%;
				display: flex;
				justify-content: space-evenly;
				position: relative;
				.back-to-top {
					position: relative;
					display: flex;
					align-items: center;
					justify-content: center;
					width: fit-content;
					margin: 0 auto;
					width: 100%;

					.to-top-notch {
						img {
							position: relative;
							z-index: 1;
							max-width: 100%;
							height: auto;
							margin-bottom: clamp(-3.25rem, -8.5393rem + 8.2645vw, -2.625rem);
						}
					}

					.content {
						cursor: pointer;
						position: absolute;
						top: 25%;
						left: 50%;
						transform: translate(-50%, -50%);
						z-index: 2;
						display: flex;
						flex-direction: column;
						align-items: center;

						.arrow {
							z-index: 2;
							display: flex;
							justify-content: center;
							margin-bottom: 0.5rem; // Adjust spacing if needed
						}

						.text {
							p {
								margin: 0;
								font-size: var(--fs-500);
								color: var(--black);
								text-align: center;
							}
						}
					}
				}
				.socials {
					width: 100%;
					ul {
						height: 100%;
						align-items: center;
						justify-content: space-evenly;
						display: flex;
						li {
							list-style-type: none;
							a {
								img {
									width: 48px;
									height: 48px;
								}
							}
						}
					}
				}
			}
		}
	}
	.mobile {
		border-radius: 25px;
		background-color: var(--green-600);
		color: var(--white);
		width: 96vw;
		margin: 100px auto 2vw auto;
		padding: 20px 0px;
		position: relative;

		.notch {
			position: absolute;
			top: -1px;
			left: 50%;
			transform: translateX(-50%);
			.container {
				position: relative;

				img {
					width: clamp(17.1875rem, 15.2425rem + 10.3734vw, 21.875rem);
				}
				.slogan {
					position: absolute;
					top: 25%;
					left: 50%;
					transform: translateX(-50%);
					text-align: center;
					text-transform: uppercase;
					font-weight: 900;
					font-size: var(--mfs-500);
					width: 100%;
					color: var(--black);
				}
			}
		}

		.content {
			display: flex;
			flex-direction: column;
			margin: 72px 0 32px 0;
			align-items: baseline;
			justify-content: space-evenly;
			gap: 40px;
			padding: 0px 20px;
			.top {
				width: 100%;
				display: flex;
				justify-content: space-between;
				.contact {
					width: 100%;
					.subtext {
						font-size: var(--mfs-300);
						margin-bottom: 16px;
					}
					h2 {
						width: fit-content;
						font-size: var(--mfs-600);
						margin-bottom: 4px;
						border-bottom: 1px solid white;
					}
					ul {
						li {
							font-size: var(--mfs-500);
							list-style-type: none;
							margin-bottom: 16px;
							a {
								display: flex;
								gap: 8px;
								align-items: center;
								img {
									width: 24px;
								}
							}
						}
					}
				}
			}
			.down {
				display: flex;
				width: 100%;
				justify-content: space-between;
				.sitemap {
					width: 100%;

					h2 {
						width: fit-content;
						font-size: var(--mfs-600);
						margin-bottom: 16px;
						border-bottom: 1px solid white;
					}
					ul {
						height: 100%;
						align-items: start;
						display: flex;
						flex-direction: column;
						gap: 24px;
						li {
							list-style-position: inside;
							font-size: var(--mfs-500);
							font-weight: 400;
						}
					}
				}
				.socials {
					width: 100%;
					display: flex;
					flex-direction: column;
					align-items: center;
					h2 {
						width: fit-content;
						font-size: var(--mfs-600);
						margin-bottom: 16px;
						border-bottom: 1px solid white;
					}
					ul {
						height: 100%;
						align-items: start;
						display: flex;
						flex-direction: column;
						gap: 16px;
						li {
							list-style-type: none;

							a {
								display: flex;
								align-items: center;
								gap: 8px;
								img {
									width: 36px;
									height: 36px;
								}
								p {
									font-size: var(--mfs-500);
									font-weight: 400;
								}
							}
						}
					}
				}
			}
		}
		a {
			color: var(--white);
			text-decoration: none;
		}
		.bottom {
			display: flex;
			position: relative;
			flex-direction: column;
			gap: 24px;
			.plug {
				margin-left: -1px;
				display: flex;
				flex-direction: column;
				.above {
					width: 32px;
					margin-bottom: -1px;
				}
				.below {
					margin-top: -1px;
					rotate: 180deg;
					transform: scaleX(-1);
					width: 32px;
				}
				p {
					width: fit-content;
					background-color: var(--white);
					padding: 2px 8px;
					border-radius: 0px 16px 16px 0px;
					a {
						color: var(--black);
					}
				}
			}
			.back-to-top {
				position: absolute;
				right: 10%;
				bottom: 50%;

				background-color: var(--white);

				display: flex;
				align-items: center;
				justify-content: center;

				border-radius: 500px;
				height: 50px;
				width: 50px;

				.arrow {
					display: flex;
					justify-content: center;
				}
			}
			.end {
				width: 100%;
				display: flex;
				align-items: center;
				justify-content: center;
				p {
					max-width: 80%;
					opacity: 0.6;
					font-size: var(--mfs-300);
				}
			}
		}
	}
</style>
