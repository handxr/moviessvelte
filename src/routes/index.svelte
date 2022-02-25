<script context="module">
	const API_KEY = import.meta.env.VITE_KEY;
	export async function load({ fetch }) {
		const response = await fetch(
			`https://api.themoviedb.org/3/movie/popular?api_key=${API_KEY}&language=en-US&page=1`
		);
		const data = await response.json();
		if (response.ok) {
			return {
				props: {
					popular: data.results
				}
			};
		}
	}
</script>

<script lang="ts">
	import { fly } from 'svelte/transition';
	import PopularMovies from '../components/PopularMovies.svelte';
	export let popular: any;
</script>

<section in:fly={{ y: 50, duration: 500, delay: 500 }} out:fly={{ duration: 500 }}>
	<PopularMovies {popular} />
</section>
