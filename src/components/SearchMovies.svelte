<script lang="ts">
	let formData = '';
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';

	const submitSearch = () => {
		goto(`/search/${formData}`);
	};
</script>

<form on:submit|preventDefault={submitSearch} class="search">
	<input bind:value={formData} name="searchMovie" type="text" placeholder="Search movie" />
	{#if formData}
		<button type="submit" out:fly={{ x: 0, duration: 500 }} in:fly={{ x: 0, duration: 500 }}
			>Search</button
		>
	{/if}
</form>

<style>
	.search {
		position: relative;
		width: 30%;
		margin: 1rem;
	}
	button {
		font-size: 0.7rem;
		padding: 0 1rem;
		background: rgb(96, 110, 201);
		color: white;
		font-weight: bold;
		border: none;
		position: absolute;
		bottom: 50%;
		right: 0;
		transform: translate(0, 50%);
		height: 100%;
		border-top-right-radius: 10px;
		border-bottom-right-radius: 10px;
		cursor: pointer;
	}
	input {
		width: 100%;
		border: none;
		font-size: 1rem;
		outline: none;
		color: rgb(255, 255, 255);
		padding: 0.5rem 0.1rem;
		transition: background 0.75s ease-out;
		font-weight: bold;
		background: rgb(63, 63, 63);
		border-radius: 10px;
		padding: 1rem;
	}
</style>
