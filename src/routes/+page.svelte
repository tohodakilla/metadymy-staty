<script>
	import graficzka from '$lib/images/graficzka.jpg'
	import logo from '$lib/images/logo.png'
</script>

<section
	style:--graficzka="url({graficzka})"
>
	<a href="/players">
		<img src={logo} alt="logo metadymy">
	</a>
</section>

<style>
	section {
		display: grid;
		place-items: center;
		width: 100%;
		height: 100vh;
		position: relative;
	}
	section::before {
		content: '';
		background-image: var(--graficzka);
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		filter: brightness(0.382);
		z-index: -1;
	}
	a {
		transition: all 369ms ease-in;
	}
	a:active {
		transform: scale(0.9)
	}
	img {
		max-width: 420px
	}
</style>