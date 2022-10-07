<script>
  import { onMount } from "svelte";

  let movies = [];

	onMount(async () => {
		const res = await fetch(`https://api.themoviedb.org/3/movie/popular?api_key=985d2210611eda826a52915c38021a1a`);
		let movies_temp = await res.json();
    movies = movies_temp.results
	});
</script>

<main>
  <h1 class="my-4 text-center">The Movies</h1>
  <div style="display: flex; flex-wrap: wrap; gap: 20px; justify-content: center; margin: 50px">
    {#each movies as movie}
    <div class="card" style="max-width: 300px;">
      <img src="https://image.tmdb.org/t/p/w500{movie.poster_path}" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{movie.title}</h5>
        <p class="card-text">{movie.overview}</p>
        <p class="card-text">Note : <span class="fw-bold">{movie.vote_average}</span></p>
        <a href="#" class="btn btn-primary">See more</a>
      </div>
    </div>
  {/each}
  </div>
</main>
