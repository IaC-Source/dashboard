<script>
	import {onMount} from 'svelte'; 
	import Chart from 'svelte-frappe-charts';
	export let name;
	onMount(async ()=> {
		const respose = await fetch('/api');
		const json = await respose.json();
		name = json.name;
	})
	let data = {
    labels: ['Sun', 'Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat'],
    datasets: [
      {
        values: [10, 12, 3, 9, 8, 15, 9]
      }
    ],
  };
  const color = ["#0000ff"];
</script>

<main>
	{#if !!name == false}
	<p> Loading ...</p>
	{:else}
	<h1>Hello {name}!</h1> 
	<Chart data={data} colors={color} type="line" />
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
		display: inline-block;
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
