<script lang="ts">
	import { language, locale } from '$lib/i18n/i18n';
	import { onMount } from 'svelte';
    import '../lib/styles/fonts.css';
	import Navbar from '../components/navbar/navbar.svelte';
	import Footer from '../components/footer/footer.svelte';

	var userLang = navigator.language;
	// nb-NO

	function setLanguage() {
		if (userLang === 'nb-NO' || userLang === 'no' || userLang === 'nn') {
			$language = 'no';
			$locale = 'no';
		} else {
			$language = 'en';
			$locale = 'en';
		}
	}

	onMount(() => {
		userLang = navigator.language || 'en'; // Default to 'en' if navigator.language is not defined.
		setLanguage();
	});
</script>

<svelte:head>
	<title>Ciao World Transport & Logistics</title>
	<meta name="description" content="FILL IN DESCRIPTION" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
	<meta name="robots" content="index, follow" />
	<meta name="content-language" content="en" />
	<meta name="keywords" content="FILL IN KEYWORDS" />
	<meta property="og:title" content="FILL IN TITLE" />
	<meta property="og:description" content="FILL IN DESCRIPTION" />
	<meta property="og:type" content="website" />
	<!--<meta property="og:url" content="https://www.domain.com" />
	 <meta property="og:image" content="https://www.domain.com/images/og-image.jpg" /> 
	<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png" />
	<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png" />
	<link rel="icon" type="image/png" sizes="192x192" href="/favicon-192x192.png" />-->
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
		--fs-400: clamp(1rem, 0.7143rem + 0.4464vw, 1.25rem);
		/* Medium text, good for body copy or subtitles */
		--fs-500: clamp(1.25rem, 0.9643rem + 0.4464vw, 1.5rem);
		/* Large text, good for subtitles or small headings */
		--fs-600: clamp(2rem, 1.7143rem + 0.4464vw, 2.25rem);
		/* Extra large, good for titles */
		--fs-700: 24px;
		/* 2X large, good for main headings */
		--fs-800: clamp(4rem, 1.5714rem + 3.7946vw, 6.125rem);

		/* // MOBILE */
		/* Smallest size, suitable for small print or tags */
		--mfs-300: 10px;
		/* Small text, good for body copy or less emphasized text */
		--mfs-400: 12px;
		/* Medium text, good for body copy or subtitles */
		--mfs-500: 14px;
		/* Large text, good for subtitles or small headings */
		--mfs-600: 18px;
		/* Extra large, good for titles */
		--mfs-700: 20px;
		/* 2X large, good for main headings */
		--mfs-800: 28px;

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
