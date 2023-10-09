<script>
	import SvelteTable from 'svelte-table'
	import { onMount } from 'svelte'
	import draft from '$lib/data/draft.csv'

	// const x = Papa.parse(draft)
	console.log(draft)
	const rows = draft
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
		}).filter(x => x !== 'date')
	}
</script>

<div class="draft">
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