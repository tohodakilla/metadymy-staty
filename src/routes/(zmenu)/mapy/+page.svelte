<script>
	import SvelteTable from 'svelte-table'
	import { onMount } from 'svelte'
	import mapy from '$lib/data/mapy.csv'

	// const x = Papa.parse(mapy)
	const rows = mapy
	let cols = []

	const calcCols = x => {
		const colNames = Object.keys(x[0])

		return colNames.map(c => {
			return {
				key: c,
				title: c,
				value: v => {
					const liczba = !isNaN(Number(v[c]))
					if(liczba) return Number(v[c])
					else return v[c]
				},
				sortable: true,
				headerClass: 'bold'
				// filterOptions: () => null
			}
		}).filter(x => x !== 'date')
	}
</script>

<div class="overall">
	<div>
		<h6>AVERAGE LENGTH</h6>
		<span>19:10</span>
	</div>
	<div>
		<h6>MEDIAN LENGTH</h6>
		<span>18:58</span>
	</div>
	<div>
		<h6>SHORTEST GAME</h6>
		<span>11:30</span>
	</div>
	<div>
		<h6>LONGEST GAME</h6>
		<span>30:52</span>
	</div>
	<div>
		<h6>FIRST PICK WIN %</h6>
		<span>46.4%</span>
	</div>
	<div>
		<h6>FIRST OBJECTIVE WIN %</h6>
		<span>58.9%</span>
	</div>
	<div>
		<h6>BLUE SIDE WIN %</h6>
		<span>55.4%</span>
	</div>
	<div>
		<h6>RED SIDE WIN %</h6>
		<span>44.6%</span>
	</div>
	<div>
		<h6>FIRST FORT WIN %</h6>
		<span>71.4%</span>
	</div>
	<div>
		<h6>FIRST KEEP WIN %</h6>
		<span>87.5%</span>
	</div>
</div>

<div class="mapy">
	<SvelteTable
		columns={calcCols(rows)}
		{rows}
	/>
</div>

<style>
	.overall {
		display: flex;
		margin-bottom: 1em;
	}
	.overall div {
		border: 1px solid var(--table-border-color);
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		align-items: center;
		flex: 1;
		text-align: center;
	}
	.overall h6 {
		margin: 0;
		/* font-weight: normal; */
	}
	.overall span {
		font-size: 1.618em;
		/* font-weight: bold; */
	}
	.mapy {
		max-height: calc(100vh - 69px - 1.618em);
		overflow: auto;
	}
</style>