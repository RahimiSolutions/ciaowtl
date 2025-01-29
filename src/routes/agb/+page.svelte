<script lang="ts">
	import Download from '$lib/icons/download.svelte';

	const deutschPdfPath = '/adsp/adsp_2017_deutsch.pdf';
	const englishPdfPath = '/adsp/adsp_2017_english.pdf';
</script>

<section class="agb">
	<h1>Conditions</h1>
	<p>
		CIAO! World Transport & Logistics UG operates exclusively on the basis of the ADSp (latest
		version) and expressly refers to the limitations of liability according to § 23.1. and § 24.1.
		<br /><br />
		The Freight Forwarder as carrier is liable for own fault only in cases of nautical fault or fire
		on board, and (3) the Freight Forwarder as carrier in the sense of the CMNI is not liable for nautical
		faults, fire on board or defects of the vessel under the conditions of Art. 25 Para. 2 CMNI.
		<br /><br />
		The registered office of the company as well as the place of jurisdiction and performance is in Hamburg.
	</p>

	<div class="pdf-downloads">
		<a href={deutschPdfPath} target="_blank" class="download-button">
			<span class="icon"><Download /></span>
			Download ADSP 2017 (Deutsch)
		</a>
		<a href={englishPdfPath} target="_blank" class="download-button">
			<span class="icon"><Download /></span>
			Download ADSP 2017 (English)
		</a>
	</div>
</section>

<style lang="scss">
	.agb {
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
		p {
			font-size: var(--fs-500);
		}
		.pdf-downloads {
			margin-top: 40px;
			display: flex;
			flex-wrap: wrap;
			gap: 1rem;

			.download-button {
				display: inline-flex;
				align-items: center;
				padding: 0.75rem 1.5rem;
				background-color: var(--green-600);
				color: white;
				text-decoration: none;
				border-radius: 4px;
				font-weight: bold;
				transition: background-color 0.3s ease;
				width: fit-content;

				&:hover {
					background-color: var(--green-500);
				}

				.icon {
					margin-right: 0.5rem;
					font-size: 1.2em;
				}
			}
		}
	}
</style>
