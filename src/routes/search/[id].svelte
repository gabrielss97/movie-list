<script context="module">
	export async function load({ params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=${import.meta.env.VITE_API}&language=en-US&query=${params.id}&page=1&include_adult=false`
		);
		const data = await res.json();
		if (res.ok) {
			return {
				props: { searchedMovie: data.results }
			};
		}
	}
</script>

<script>
	import MovieCard from '../../components/MovieCard.svelte';
	export let searchedMovie;
</script>

{#await searchedMovie}
<h1>Carregando...</h1>

{:then searchedMovie}
<div class="searched-movies">
	{#each searchedMovie as movie}
		<MovieCard {movie} />
	{/each}
</div>
{:catch error}
<h1>Erro!</h1>
{/await}

<style>
	.searched-movies {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
		grid-column-gap: 2.5rem;
		grid-row-gap: 2rem;
	}

</style>
