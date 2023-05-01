<script lang="ts">
	import { onMount } from 'svelte';
	//import secomppList from '../../../static/lista-secompps.json';

	const url = './lista-secompps.json';

	let secomppList: SecomppList[] = [];

	onMount(async () => {
		const response = await fetch(url);
		secomppList = await response.json();
	});

	interface SecomppList {
		name: string;
		year: string;
		date: string;
		description: string;
	}
</script>

{#each secomppList as item}
	## {item.year}
	**{item.name}**
	{item.date}

	{item.description}

	- [Site](./{item.year})

	<hr />
{:else}
	<p>Carregando...</p>
{/each}
