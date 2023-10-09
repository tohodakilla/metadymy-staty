<script>
	import SvelteTable from 'svelte-table'
	import { onMount } from 'svelte'
	import playersCSV from '$lib/data/player_statistics.csv'

	// const x = Papa.parse(playersCSV)
	console.log(playersCSV)
	const rows = playersCSV
	let cols = []

	const calcCols = x => {
		const colNames = Object.keys(x[0])

		return colNames.map(c => {
			return {
				key: c,
				title: c,
				value: v => v[c],
				sortable: true,
				headerClass: 'bold'
				// filterOptions: () => null
			}
		})
	}
</script>

<div>
	<SvelteTable
		columns={calcCols(rows)}
		{rows}
	/>
</div>

<style>
	div {
		max-height: calc(100vh - 69px - 1.618em);
		overflow: auto;
	}
</style>