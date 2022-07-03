<!-- 
	// const SEARCHAPI =
	// 	'https://api.themoviedb.org/3/search/movie?&api_key=04c35731a5ee918f014970082a0088b1&query=';
 -->
<script context="module">
	export async function load({ fetch }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=04c35731a5ee918f014970082a0088b1&page=1`
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
	export let movies;
</script>

<!-- --------------------------- HTML------------------------- -->

<section>
	<SearchMovies />
	<PopularMovies {movies} />
</section>