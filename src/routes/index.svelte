<script context="module">
	export async function load({ fetch }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=${import.meta.env.VITE_API}&page=1`
		);
		const data = await res.json();
		if (res.ok) {
			return {
				props: { movies: data.results }
			};
		}
	}
</script>

<script>
    
	import PopularMovies from '../components/PopularMovies.svelte';
	import SearchMovies from '../components/SearchMovies.svelte';
	import { fly } from 'svelte/transition'
    export let movies;

</script>

<!-- --------------------------- HTML------------------------- -->

<section  out:fly={{ duration:500}}>
    <!-- in:fly={{y:200, duration: 500}} -->
	<SearchMovies />
	<PopularMovies {movies} />
</section>

<style>
    section {
        opacity: 0;
        transform: translateY(-200px);
        animation: fadein .5s ease-out forwards;
    }

    @keyframes fadein {
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }
</style>