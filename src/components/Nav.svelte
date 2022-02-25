<script lang="ts">
	import SearchMovies from '../components/SearchMovies.svelte';
</script>

<nav>
	<SearchMovies />
	<a href="/">Movie Database</a>
</nav>

<style>
	nav {
		display: flex;
		min-height: 10vh;
		align-items: center;
		justify-content: center;
	}
	a {
		font-size: 1rem;
		font-weight: bold;
		color: black;
		text-decoration: none;
	}
</style>
