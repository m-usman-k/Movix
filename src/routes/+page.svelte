<script>
	let searchTerm = '';
	let allMovies = [
		{
			title: "Inception",
			year: 2010,
			poster: "https://m.media-amazon.com/images/I/51oDblB5m9L._AC_.jpg"
		},
		{
			title: "Interstellar",
			year: 2014,
			poster: "https://m.media-amazon.com/images/I/71n58Q4Zl3L._AC_SY679_.jpg"
		},
		{
			title: "The Matrix",
			year: 1999,
			poster: "https://m.media-amazon.com/images/I/51EG732BV3L._AC_.jpg"
		},
		{
			title: "Tenet",
			year: 2020,
			poster: "https://m.media-amazon.com/images/I/81p+xe8cbnL._AC_SY679_.jpg"
		}
	];

	// Filtered movie list
	$: filteredMovies = allMovies.filter(movie =>
		movie.title.toLowerCase().includes(searchTerm.toLowerCase())
	);
</script>

<style>
	/* Reset */
	* {
		margin: 0;
		padding: 0;
		box-sizing: border-box;
        font-family: Arial, sans-serif;
	}

	nav {
		background-color: #111;
		color: #fff;
		padding: 1rem 2rem;
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	nav h1 {
		font-size: 1.8rem;
		font-weight: bold;
		color: #f8c200;
	}

	.nav-wrapper ul.nav {
		display: flex;
		gap: 1.5rem;
		list-style-type: none;
	}

	.nav-wrapper ul.nav li {
		cursor: pointer;
		padding: 0.4rem 1rem;
		border-radius: 5px;
		transition: background 0.3s, color 0.3s;
	}

	.nav-wrapper ul.nav li:hover {
		background-color: #333;
		color: #f8c200;
	}

	.hero {
		padding: 8rem 2rem;
		background: linear-gradient(to right, #000000cc, #222222cc), url('https://wallpaperaccess.com/full/329583.jpg');
		background-size: cover;
		background-position: center;
		color: white;
		text-align: center;
	}

	.hero h2 {
		font-size: 3rem;
		margin-bottom: 1rem;
		text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7);
	}

	.hero p {
		font-size: 1.2rem;
		text-shadow: 1px 1px 4px rgba(0, 0, 0, 0.6);
	}

	.search-bar {
		margin: 2rem auto;
		text-align: center;
	}

	input[type="text"] {
		padding: 0.6rem 1rem;
		width: 300px;
		border-radius: 5px;
		border: 1px solid #ccc;
		font-size: 1rem;
	}

	.grid {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
		gap: 1.5rem;
		padding: 2rem;
	}

	.card {
		background: #fff;
		border-radius: 8px;
		box-shadow: 0 2px 8px rgba(0,0,0,0.1);
		overflow: hidden;
		text-align: center;
		transition: transform 0.2s ease;
	}

	.card:hover {
		transform: scale(1.03);
	}

	.card img {
		width: 100%;
		height: auto;
	}

	.card h3 {
		margin: 0.5rem 0;
		font-size: 1.1rem;
	}

	.card p {
		color: #555;
		font-size: 0.9rem;
		margin-bottom: 1rem;
	}

	footer {
		background-color: #111;
		color: #ccc;
		text-align: center;
		padding: 1.5rem;
		margin-top: 2rem;
		font-size: 0.9rem;
	}
</style>

<!-- Navbar -->
<nav>
	<h1>🎬 Movix</h1>
	<div class="nav-wrapper">
		<ul class="nav">
			<li>Genre</li>
			<li>Movies</li>
			<li>Watchlist</li>
		</ul>
	</div>
</nav>

<!-- Hero Section -->
<section class="hero">
	<h2>Welcome to the Ultimate Movie Gallery</h2>
	<p>Discover movies, search your favorites, and enjoy!</p>
</section>

<!-- Search Bar -->
<div class="search-bar">
	<input
		type="text"
		placeholder="Search movies..."
		bind:value={searchTerm}
	/>
</div>

<!-- Movie Cards -->
<div class="grid">
	{#if filteredMovies.length > 0}
		{#each filteredMovies as movie}
			<div class="card">
				<img src={movie.poster} alt={movie.title} />
				<h3>{movie.title}</h3>
				<p>Released: {movie.year}</p>
			</div>
		{/each}
	{:else}
		<p style="grid-column: 1/-1; text-align: center;">No movies found.</p>
	{/if}
</div>

<!-- Footer -->
<footer>
	&copy; {new Date().getFullYear()} Movix. All rights reserved.
</footer>
