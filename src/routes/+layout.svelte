<script lang="ts">
    import '../lib/styles/fonts.css';
	import Navbar from '../components/navbar/navbar.svelte';
	import Footer from '../components/footer/footer.svelte';

</script>

<svelte:head>
	<title>Ciao World Transport & Logistics</title>
	<meta name="description" content="No matter where your cargo needs to go, we have the infrastructure to deliver it effectively." />
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<meta name="robots" content="index, follow" />
	<meta name="content-language" content="en" />
	<meta name="keywords" content="Logistics, International shipping, Transportation, Freight forwarding, import, export, Hamburg, Germany, International transport" />
	<meta property="og:title" content="Transport Made Easy - CIAO" />
	<meta property="og:description" content="From A to Z, we handle your shipments with care and precision." />
	<meta property="og:type" content="website" />
	<!--<meta property="og:url" content="https://www.domain.com" />
	 <meta property="og:image" content="https://www.domain.com/images/og-image.jpg" /> -->
	<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
	<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
	<link rel="icon" type="image/png" sizes="192x192" href="/favicon-192x192.png" />
	<link rel="icon" type="image/svg+xml" href="/favicon.png" />
</svelte:head>

<Navbar />
<slot />
<Footer />

<style>
	:global(*) {
		--white: #fff;
		--black-200: rgba(30, 30, 30, 0.05);
		--black: #1E1E1E;
        font-family: 'Sfpro';

		--blue-200: rgba(67, 86, 100, 0.3);
		--blue-400: #435664;
		--green-100: rgba(185, 210, 214, 0.3);
		--green-200: rgba(201, 223, 221, 0.5);
		--green-400: #C9DFDD;
		--green-500: #487D78;
		--green-600: #132320;

		/* Smallest size, suitable for small print or tags */
		--fs-300: 12px;
		/* Small text, good for body copy or less emphasized text */
		--fs-400: clamp(1rem, 0.7143rem + 0.4464vw, 1rem);
		/* Medium text, good for body copy or subtitles */
		--fs-500: clamp(1.25rem, 0.9643rem + 0.4464vw, 1.25rem);
		/* Large text, good for subtitles or small headings */
		--fs-600: clamp(2rem, 1.7143rem + 0.4464vw, 2.25rem);
		/* Extra large, good for titles */
		--fs-700: 24px;
		/* 2X large, good for main headings */
		--fs-800: clamp(3.75rem, 2.3214rem + 2.2321vw, 5rem);

		--fs-slogan:clamp(1.5rem, 0.6429rem + 1.3393vw, 2.25rem); 



		/* // MOBILE */
		/* Smallest size, suitable for small print or tags */
		--mfs-300: clamp(0.625rem, 0.5731rem + 0.2766vw, 0.75rem);
		/* Small text, good for body copy or less emphasized text */
		--mfs-400: clamp(0.875rem, 0.8231rem + 0.2766vw, 1rem);
		/* Medium text, good for body copy or subtitles */
		--mfs-500: clamp(1rem, 0.9481rem + 0.2766vw, 1.125rem);
		/* Large text, good for subtitles or small headings */
		--mfs-600: clamp(1.3125rem, 1.2347rem + 0.4149vw, 1.5rem);
		/* Extra large, good for titles */
		--mfs-700: clamp(2rem, 1.8963rem + 0.5533vw, 2.25rem);


		margin: 0;
		padding: 0;
		box-sizing: border-box;
		scroll-behavior: smooth;
	}
	:global(body) {
		background-color: var(--white);
	}

	/* Scrollbar Styles */
	/* For Webkit browsers */
	:global(::-webkit-scrollbar) {
		width: 12px; /* Width of the scrollbar */
		height: 12px; /* Height of the scrollbar */
	}

	:global(::-webkit-scrollbar-track) {
		background: var(--black-200); /* Background of the scrollbar track */
		border-radius: 10px; /* Rounded corners for the track */
	}

	:global(::-webkit-scrollbar-thumb) {
		background-color: var(--green-500); /* Color of the scrollbar thumb */
		border-radius: 10px; /* Rounded corners for the thumb */
		border: 3px solid var(--black-200); /* Space around the thumb */
	}

	:global(::-webkit-scrollbar-thumb:hover) {
		background-color: var(--green-600); /* Color of the scrollbar thumb on hover */
	}
</style>
