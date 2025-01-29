<script lang="ts">
	import Download from '$lib/icons/download.svelte';

	const deutschPdfPath = '/adsp/adsp_2017_deutsch.pdf';
	const englishPdfPath = '/adsp/adsp_2017_english.pdf';
</script>

<section class="privacy-policy">
	<h1>Privacy Policy</h1>
	<p>Last Updated: 29.01.2025</p>
	<article>
		<h2>1. Introduction</h2>
		<p>
			Ciao ("we," "us," or "our") operates the website https://www.ciaowtl.com/ and is committed to
			protecting your privacy under the EU General Data Protection Regulation (GDPR) and the German
			Federal Data Protection Act (BDSG). This policy explains how we handle data when you use our
			website.
		</p>
		<p>Key Points:</p>
		<ul>
			<li>We do not collect, store, or process any personal data.</li>
			<li>We use a third-party service (Elfsight) solely to display Google Reviews.</li>
			<li>You have rights under GDPR; we explain how to exercise them below.</li>
		</ul>
	</article>

	<hr />

	<article>
		<h2>2. Data Controller and Legal Basis</h2>
		<section>
			<h4>Data Controller:</h4>
			<address>
				<ul>
					<li>CIAO! World Transport & Logistics UG</li>
					<li>Wendenstraße 435, 20537 Hamburg, Germany</li>
					<li>info@ciao-wtl.com</li>
					<li>+49 4075 695565</li>
				</ul>
			</address>
		</section>
		<section>
			<h4>Legal Basis for Processing via Elfsight:</h4>
			<p>
				The integration of Elfsight's widget is based on our legitimate interest (Art. 6(1)(f) GDPR)
				to provide user-generated reviews for transparency and website functionality.
			</p>
		</section>
	</article>

	<hr />

	<article>
		<h2>3. Third-Party Services: Elfsight</h2>
		<p>
			Our website uses Elfsight's widget to display Google Reviews. Elfsight, as an independent data
			processor, may collect:
		</p>
		<ul>
			<li>IP address</li>
			<li>Operating system</li>
			<li>Browser type</li>
		</ul>
		<section>
			<h4>Elfsight's Data Handling:</h4>
			<ul>
				<li>
					<strong>Purpose:</strong> Security, troubleshooting, and service functionality (Art. 5 GDPR).
				</li>
				<li><strong>Retention:</strong> Data is anonymized and stored for 7 days.</li>
				<li>
					<strong>No Marketing:</strong> Data is not used for tracking or shared with third parties.
				</li>
				<li>
					<strong>International Transfers:</strong> Elfsight uses Google Cloud Platform (global servers).
					Data transfers comply with GDPR safeguards (e.g., adequacy decisions or Standard Contractual
					Clauses).
				</li>
			</ul>
		</section>
		<section>
			<h4>Your Rights with Elfsight:</h4>
			<p>
				To exercise GDPR rights (access, rectification, deletion), contact Elfsight directly via
				[link to their Privacy Policy].
			</p>
		</section>
		<p>
			<strong>Disclaimer:</strong> We are not responsible for Elfsight's data practices. Their services
			are essential for our website; functionality may be impacted if restricted.
		</p>
	</article>

	<hr />

	<article>
		<h2>4. Your GDPR Rights</h2>
		<p>Even though we do not collect data, you have the right to:</p>
		<ul>
			<li>Request access to data processed by third parties (e.g., Elfsight).</li>
			<li>
				Lodge complaints with a supervisory authority (e.g., German Federal Commissioner for Data
				Protection).
			</li>
		</ul>
	</article>

	<hr />

	<article>
		<h2>5. Data Security</h2>
		<p>
			We implement technical measures (e.g., HTTPS) to protect our website. Elfsight encrypts data
			and adheres to industry standards.
		</p>
	</article>

	<hr />

	<article>
		<h2>6. Changes to This Policy</h2>
		<p>Updates will be posted here. Material changes may be notified via email (if feasible).</p>
	</article>

	<hr />

	<article>
		<h2>7. Contact Us</h2>
		<p>For privacy-related inquiries:</p>
		<address>
			CIAO! World Transport & Logistics UG<br />
			Wendenstraße 435, 20537 Hamburg, Germany<br />
			info@ciao-wtl.com<br />
			+49 4075 695565
		</address>
		<br/>
		<p>For GDPR-specific requests, contact Elfsight directly.</p>
	</article>
</section>

<style lang="scss">
	.privacy-policy {
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
		h2 {
			font-size: var(--fs-600);
			color: var(--green-600);
			font-weight: 400;
			margin-bottom: 24px;
		}
		h4 {
			margin: 24px 0;
			color: var(--green-600);
			font-weight: 700;
		}
		article {
			margin-top: 36px;
			font-size: var(--fs-500);
		}

		ul{
			list-style-position: inside;
		}

		hr{
			margin: 36px 0;
		}
	}
</style>
