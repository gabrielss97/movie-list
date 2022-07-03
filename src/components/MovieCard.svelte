<script>
	export let movie;

	const { title, poster_path, release_date, id } = movie;
</script>

<!-- HTML  -->

<div class="movie-card">
	<a sveltekit:prefetch sveltekit:noscroll href={'/movie/' + id}>
		<img src={`https://image.tmdb.org/t/p/w500` + poster_path} alt={title} />
		<div class="description">
			<h2>{title}</h2>
			<p>{release_date}</p>
		</div>
	</a>
</div>

<!-- CSS  -->
<style>
	img {
		width: 100%;
		height: 50vh;
		object-fit: cover;
		border-radius: 1rem;
	}

	a {
		text-decoration: none;
	}

	h2 {
		padding: 1rem 0 0.5rem;
	}

	p {
		color: rgb(162, 162, 162);
	}

	.movie-card {
		border-radius: 1rem;
	}

	.movie-card:hover img {
		box-shadow: 0px 0px 20px 0px rgba(0, 0, 0, 0.947);
		transition: box-shadow 1s cubic-bezier(0.075, 0.82, 0.165, 1) 0s,
			transform 1s cubic-bezier(0.075, 0.82, 0.165, 1) 0s;
	}

	.description {
		padding: 0.5rem;
	}
</style>
