<script context="module">
	

	export async function load({ fetch, params }) {
		const response = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${import.meta.env.VITE_KEY}&language=en-US&query=${params.id}&page=1&include_adult=false`
		);
		const data = await response.json();
		if (response.ok) {
			return {
				props: {
					searchedMovie: data.results
				}
			};
		}
	}
</script>

<script lang="ts">
	import MovieCard from './../../components/MovieCard.svelte';
	export let searchedMovie: any;
</script>

<div class="searched-movies">
	{#each searchedMovie as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
	.searched-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 1rem auto;
		grid-row-gap: 2rem;
		height: 20vh;
	}
</style>
