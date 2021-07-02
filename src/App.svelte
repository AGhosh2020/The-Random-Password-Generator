
<script>
	import Header from './components/header/header.svelte';
	import Footer from './components/footer/footer.svelte';
	import RanPassGen from './components/ranpassgen.svelte';
</script>
<svelte:head>
    <link href="https://fonts.googleapis.com/css2?family=Josefin+Sans" rel="stylesheet">
</svelte:head>
<main>
	<Header/>
	<RanPassGen />
	<Footer/>
</main>

<style>
	:root{
		--bg-color: #FFFFFF;
		--text-color: #000000;
	}
	:global(body) {
		font-family: 'Josefin Sans', sans-serif;
		text-align: center;
		background: var(--bg-color);
		color:var(--text-color);
		transition: background-color 0.9s;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
	:global(body.dark) {
		background-color: black;
		color: rgb(167, 167, 167);
	}
</style>