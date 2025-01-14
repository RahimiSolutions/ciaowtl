<script lang="ts">
	import { fade } from 'svelte/transition';

	let showToast = false;
	let toastMessage = '';

	function handleCopy(text: string) {
		copyToClipboard(text);
		toastMessage = 'Copied to clipboard!';
		showToast = true;
		setTimeout(() => (showToast = false), 3000);
	}

	function copyToClipboard(text: string) {
		const textArea = document.createElement('textarea');
		textArea.value = text;
		textArea.select();
		textArea.setSelectionRange(0, 99999);
		navigator.clipboard.writeText(textArea.value);
	}
</script>

<section class="imprint">
	<h1>Imprint</h1>

	<div class="company-info">
		<div class="title"><h2>CIAO - WTL</h2></div>
		<p>
			Company: CIAO! World Transport & Logistics UG <button
				on:click={() => handleCopy('CIAO! World Transport & Logistics UG')}>Copy</button
			>
		</p>
		<p>
			Adress: Wendenstraße 435, 20537 Hamburg, Germany <button
				on:click={() => handleCopy('Wendenstraße 435, 20537 Hamburg, Germany')}>Copy</button
			>
		</p>
	</div>

	<div class="contact-info">
		<div class="title"><h2>Contact Information</h2></div>
		<p>
			Email: <a href="mailto:info@ciao-wtl.com">info@ciao-wtl.com</a>
			<button on:click={() => handleCopy('info@ciao-wtl.com')}>Copy</button>
		</p>
		<p>
			Phone: <a href="tel:+494075695565">+49 4075 695565</a>
			<button on:click={() => handleCopy('+49 4075 695565')}>Copy</button>
		</p>
	</div>

	<div class="managing-director">
		<div class="title"><h2>Managing Director | Geschäftsführer</h2></div>
		<p>Ahmad Alkhatib</p>
	</div>

	<div class="ٌregistry-entry">
		<div class="title"><h2>Registry Entry</h2></div>
		<p>
			Handelsregister | Company Registration: HRB 181567 Gerichtsstand | Court of Law: Hamburg,
			Germany
			<button
				on:click={() => handleCopy('HRB 181567 Gerichtsstand | Court of Law: Hamburg, Germany')}
				>Copy</button
			>
		</p>
	</div>

	<div class="vat">
		<div class="title"><h2>VAT Identification Number</h2></div>
		<p>DE362361361 <button on:click={() => handleCopy('DE362361361')}>Copy</button></p>
	</div>

	<div class="responsible">
		<div class="title"><h2>Responsible for Content (§ 55 Abs. 2 RStV):</h2></div>
		<p>Ahmad Alkhatib</p>
	</div>

	<!-- Toast for copy confirmation -->
	{#if showToast}
		<div class="toast" transition:fade>{toastMessage}</div>
	{/if}
</section>

{#if showToast}
	<div class="toast" transition:fade>
		{toastMessage}
	</div>
{/if}

<style lang="scss">
	button {
		background-color: var(--green-600);
		color: #fff;
		border: none;
		border-radius: 5px;
		padding: 5px 10px;
		cursor: pointer;
		margin-left: 10px;
		font-size: 0.9rem;
		transition: background-color 0.3s;
	}

	button:hover {
		background-color: var(--green-500);
	}

	.toast {
		position: fixed;
		bottom: 20px;
		right: 20px;
		background-color: #333;
		color: white;
		padding: 10px 20px;
		border-radius: 5px;
		z-index: 1000;
	}
	.imprint {
		// General page styling
		padding-top: 100px; // Adds space at the top of the page
		width: 80%;
		margin: auto;
		line-height: 1.3;
		color: var(--black);
		h1 {
			font-size: var(--fs-800);
			color: var(--green-600);
			font-weight: 400;
		}
		.title {
			h2 {
				font-size: var(--fs-500);
				color: var(--green-500); // Light blue for titles
				margin-bottom: 10px;
				text-transform: uppercase;
			}
		}

		// Section styling
		.company-info,
		.contact-info,
		.managing-director,
		.ٌregistry-entry,
		.vat,
		.responsible {
			margin-bottom: 30px; // Space between sections
			padding: 10px 20px;
			border: 1px solid #ddd;
			border-radius: 8px;
			background-color: #f9f9f9;
			font-size: var(--fs-400);
			font-weight: 500;

			p {
				margin: 5px 0;
			}
		}
		a {
			text-decoration: none;
			color: #333;

			&:hover {
				color: var(--green-500);
				font-weight: 600;
			}
		}
	}
	* {
		transition: all 0.2s ease-in-out;
	}
</style>
