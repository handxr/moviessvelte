<script context="module">
	export async function load({ fetch, params }) {
		const response = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=${
				import.meta.env.VITE_KEY
			}&language=en-US`
		);
		const data = await response.json();
		if (response.ok) {
			return {
				props: {
					movie: data
				}
			};
		}
	}
</script>

<script lang="ts">
	import { fly } from 'svelte/transition';
	export let movie: any;
</script>

<div
	class="movie-details"
	in:fly={{ y: 50, duration: 500, delay: 500 }}
	out:fly={{ duration: 500 }}
>
	<div class="img-container">
		<img src={`https://image.tmdb.org/t/p/original${movie.backdrop_path}`} alt={movie.title} />
	</div>
	<div class="txt-container">
		<h1>{movie.title}</h1>
		<p class="overview">{movie.overview}</p>
		<p>
			<span>Release Date</span>
			{movie.release_date} <br />
			<span>Budget:</span> ${movie.budget} <br />
			<span>Rating:</span>
			{movie.vote_average}<br />
			<span>Runtime:</span>
			{movie.runtime}mins
		</p>
	</div>
</div>

<style>
	h1 {
		padding: 1rem 0 2rem;
	}
	p {
		padding: 1rem 0;
	}
	.img-container {
		width: 100%;
	}
	img {
		width: 100%;
		border-radius: 1rem;
	}
	.movie-details {
		margin: 2rem 20%;
	}
	span {
		font-weight: bold;
	}
</style>
