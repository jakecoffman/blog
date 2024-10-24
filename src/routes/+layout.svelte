<script>
	export const prerender = true; // set for a static build
	const { children } = $props();
</script>

<nav>
	<ul>
		<li>
			<a href="/">Home</a>
		</li>
	</ul>
</nav>

{@render children()}

<!--Add padding at bottom of the page-->
<div style="padding-bottom: 5em;"></div>

<style>

	ul {
		list-style: none;
		padding: 0;
		margin: 0;
		display: flex;
		justify-content: center;
		gap: 1em;
	}

	li {
		display: inline;
	}
</style>
