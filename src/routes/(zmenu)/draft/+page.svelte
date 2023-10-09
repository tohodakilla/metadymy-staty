<script>
	import SvelteTable from 'svelte-table'
	import { onMount } from 'svelte'
	import draft from '$lib/data/draft.csv'

	// const x = Papa.parse(draft)
	const rows = draft
	let cols = []

	const calcCols = x => {
		const colNames = Object.keys(x[0])

		return colNames.map(c => {
			return {
				key: c,
				title: c,
				value: v => {
					const isProcent = v[c].split('%').length > 1
					const liczba = !isNaN(Number(v[c]))

					if(liczba) return Number(v[c])
					else {
						if(isProcent) return Number(v[c].split('%')[0])
						else return v[c]
					}
				},
				renderValue: v => v[c],
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