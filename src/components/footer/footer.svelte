<script>
	import notch from '$lib/images/top-notch.svg';
	import logo from '$lib/images/logo.png';
	import backToTop from '$lib/images/ToTopNotch.svg';
	import Arrow from '$lib/icons/arrow.svelte';
</script>

<footer>
	<div class="notch">
		<div class="container">
			<img src={notch} alt="scalable vector graphic of a top notch" />
			<div class="slogan"><p>Time is money, <br /> and we save you both</p></div>
		</div>
	</div>
	<div class="logo">
		<img src={logo} alt="logo Ciao World Transport & Logistics" />
	</div>
	<div class="content">
		<div class="left">
			<div class="contact">
				<h2>Contact Us</h2>
				<ul>
					<li>info@ciao-wtl.com</li>
					<li>+49 4075 695565</li>
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
					<li><a href="/">Containers</a></li>
					<li><a href="/">Contact</a></li>
				</ul>
			</div>
			<div class="links">
				<ul>
					<li><a href="/">Get a Quote</a></li>
					<li><a href="/">Imprint</a></li>
				</ul>
			</div>
		</div>
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
			<div class="socials"></div>
		  </div>
	</div>
</footer>

<style lang="scss">
	footer {

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
		a{
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

					.to-top-notch {
						img {
							position: relative;
							z-index: 1;
							max-width: 100%;
							height: auto;
							margin-bottom: -42px;
						}
					}

					.content { cursor: pointer;
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
				}
			}
		}
	}
</style>
