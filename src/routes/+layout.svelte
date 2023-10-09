<script>
  import '../app.scss'
</script>

<main>
	<div class="content">
		<slot />
	</div>
</main>

<style lang=scss>
	:global(::-webkit-scrollbar) {
		width: 6px;
		height: 6px;
	}
	:global(::-webkit-scrollbar-thumb) {
		background: var(--primary);
		border-radius: 9px;
	}
	:global(::-webkit-scrollbar-thumb:hover) {
		background: var(--primary);
	}
	:global(::-webkit-scrollbar-track) {
		background: var(--primary-700);
		border-radius: 9px;
	}
	main {
		display: grid;
		min-width: 100%;
		padding: 0!important;
		margin: 0;
		background: var(--primary-700)
	}
	.content {
		max-height: fit-content;
		overflow: auto;
	}
</style>