<script context="module">
	export async function load({ fetch, params }) {
		const res = await fetch(
			`https://api.themoviedb.org/3/movie/${params.id}?api_key=04c35731a5ee918f014970082a0088b1&language=en-US`
		);
		const movieDetail = await res.json();
		if (res.ok) {
			return {
				props: { movieDetail }
			};
		}
	}
</script>

<script>
	export let movieDetail;
	const {
		title,
		overview,
		release_date,
		vote_average,
		budget,
		runtime,
		backdrop_path
	} = movieDetail;
</script>

<div class="movie-details">
	<div class="img-container">
		<img src={`https://image.tmdb.org/t/p/w1280` + backdrop_path} alt={title} />
	</div>
	<div class="txt-container">
		<h1>{title}</h1>
		<p class="overview">
			<span>Overview:</span>
			{overview}
		</p>
		<p>
			<span>Release Date:</span>
			{release_date} <br />
			<span>Budget:</span>
			{budget} <br />
			<span>Rating:</span>
			{vote_average} <br />
			<span>Runtime:</span>
			{runtime}min <br />
		</p>
	</div>
</div>

<style>
	.movie-details {
		padding: 4rem 10%;
	}

	.img-container {
		text-align: center;
		margin-bottom: 2rem;
	}

	h1 {
		text-align: center;
		margin-bottom: 1rem;
	}

	p {
		margin-bottom: 0.5rem;
	}

	span {
		font-weight: bold;
		line-height: 1.8rem;
	}

	img {
		width: 100%;
		border-radius: 1rem;
	}

	@media (max-width: 560px) {
		img {
			width: 100%;
		}
	}
</style>
