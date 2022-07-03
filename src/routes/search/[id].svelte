<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/search/movie?api_key=04c35731a5ee918f014970082a0088b1&language=en-US&query=${params.id}&page=1&include_adult=false`
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

<div class="searched-movies">
	{#each searchedMovie as movie}
		<MovieCard {movie} />
	{/each}
</div>

<style>
    .searched-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap: 2.5rem;
        grid-row-gap: 2rem;
        transform: translateY(-200px);
        animation: dropdown .8s ease-out forwards;
        opacity: 0;
    }

    @keyframes dropdown {
        to {
            transform: translateY(0);
            opacity: 1;
        }
    }
</style>