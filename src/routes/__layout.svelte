<script lang="ts">
	import Header from '$lib/components/Header.svelte';
	import Footer from '$lib/components/Footer.svelte';
</script>
<style>
	main{
		height: max-content;
	}
</style>
<Header />

<main>
	<slot />
</main>

<Footer />