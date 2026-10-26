<script lang="ts">
	import Header from '#lib/components/Header.svelte';
	import Hero from '#lib/components/Hero.svelte';
	import Stats from '#lib/components/Stats.svelte';
	import Sleep from '#lib/components/Sleep.svelte';
	import Inside from '#lib/components/Inside.svelte';
	import Features from '#lib/components/Features.svelte';
	import WagReport from '#lib/components/WagReport.svelte';
	import Reviews from '#lib/components/Reviews.svelte';
	import Pricing from '#lib/components/Pricing.svelte';
	import Faq from '#lib/components/Faq.svelte';
	import Preorder from '#lib/components/Preorder.svelte';
	import Footer from '#lib/components/Footer.svelte';
</script>

<svelte:head>
	<title>Whoof — the quantified dog</title>
	<meta
		name="description"
		content="Whoof is the health tracker for dogs: sleep, activity, heart rate and the precise number of zoomies, measured on the collar."
	/>
</svelte:head>

<Header />
<main>
	<Hero />
	<Stats />
	<Sleep />
	<Inside />
	<Features />
	<WagReport />
	<Reviews />
	<Pricing />
	<Faq />
	<Preorder />
</main>
<Footer />
