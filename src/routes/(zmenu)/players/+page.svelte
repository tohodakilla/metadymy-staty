<script>
	import SvelteTable from 'svelte-table'
	import { onMount } from 'svelte'
	import playersCSV from '$lib/data/player_statistics.csv'

	// const x = Papa.parse(playersCSV)
	const rows = playersCSV
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
				// renderValue: v => {
				// 	if(c.includes('%')) return Number() + '%'
				// 	else return v[c]
				// 	const isProcent = v[c].split('%').length > 1
				// },
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