<script>
	import {onMount} from 'svelte';
	export let name;
	onMount(async ()=> {
		const respose = await fetch('/api');
		const json = await respose.json();
		name = json.name;
	})
</script>

<main>
	{#if !!name == false}
	<p> 로딩중인데?</p>
	{:else}
	<h1>Hello {name}!</h1>
	<img alt="helm images" src="/helm-horizontal-color.png">
	<h2>I am J.A.R.V.I.S </h2>
        <h2>How could I manage your k8s package.</h2>
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #0000ff;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	h2 {
		color: #bb33ff;
		font-size: 3em;
		font-weight: 30;
	}

	img {
		width: 150px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
