<script>
	export let movies;
	import MovieCard from './MovieCard.svelte';
</script>

<!-- HTML -->

<h3>Popular Movies</h3>

<div class="popular-movies">
	{#each movies as movie}
		<MovieCard {movie}/>
	{:else}
		<p>Loading...</p>
	{/each}
</div>

<!-- CSS -->

<style>
    h3 {
        font-size: 1.2rem;
        padding: 1rem 0;
        transform: translateY(-200px);
        animation: dropdown .8s ease-out forwards;
        opacity: 0;
    }

    .popular-movies {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        grid-column-gap: 2.5rem;
        grid-row-gap: 2rem;
    }

</style>