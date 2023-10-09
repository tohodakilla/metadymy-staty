<script>
	import logo from '$lib/images/logo.png'
	import { page } from '$app/stores'

	$: ({ url } = $page)
</script>

<div class="wrapper">
	<nav>
		<div class="container">
			<img src={logo} alt="logo metadymy" style:height=69px>
			
			<ul>
				<li><a class:active={url.pathname === '/players'} href="/players">playery ogolne</a></li>
				<li><a class:active={url.pathname === '/draft'} href="/draft">draft</a></li>
				<li><a class:active={url.pathname === '/teams'} href="/teams">teams</a></li>
				<li><a class:active={url.pathname === '/mapy'} href="/mapy">mapy</a></li>
			</ul>
		</div>
	</nav>
	
	<div class="container kontent">
		<slot />
	</div>
</div>

<style>
	.wrapper {
		display: grid;
		grid-template-rows: 69px 1fr ;
		height: 100%;
	}
	nav {
		background: var(--nav-background-color);
		backdrop-filter: saturate(180%) blur(20px);
		box-shadow: 0 1px 0 var(--nav-border-color);
	}
	nav ul {
		display: flex;
		align-items: center;
	}
	nav .container {
		display: flex;
		justify-content: space-between;
	}
	.container {
		width: 100%;
		max-width: 1280px;
		margin: 0 auto;
	}
	a {
		color: var(--accordion-open-summary-color);
		
	}
	a.active {
		color: var(--accordion-close-summary-color);
		font-weight: bold;
	}

	.kontent {
		padding-top: 1em;
	}
</style>