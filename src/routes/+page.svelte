<script lang="ts">
	import { fade } from 'svelte/transition';
	import { artist } from '$lib/artist.config';
	import Song from '$lib/components/Song.svelte';
	import Heading from '$lib/components/Heading.svelte';

	let heroVisible = $state(false);
	$effect(() => {
		setTimeout(() => {
			heroVisible = true;
		}, 350);
	});
</script>

<!-- ═══════════════════════════════════════════════════════════════════════ -->
<!-- HERO                                                                   -->
<!-- ═══════════════════════════════════════════════════════════════════════ -->
<section id="hero" style="background-image: url({artist.heroBackground})">
	<div class="hero-overlay"></div>

	{#if heroVisible}
		<div class="hero-logo-wrap" transition:fade={{ duration: 900 }}>
			<img src={artist.logo} alt={artist.name} class="hero-logo" />
		</div>
	{/if}

	<div class="hero-content">
		<p class="hero-genre">{artist.genre}</p>
		<h1 class="hero-name">{artist.name.toUpperCase()}</h1>
		<p class="hero-tagline">{artist.tagline.toUpperCase()}</p>
	</div>

	<div class="scroll-hint">
		<span class="scroll-line"></span>
		<span class="scroll-text">SCROLL</span>
	</div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════ -->
<!-- MUSIC                                                                  -->
<!-- ═══════════════════════════════════════════════════════════════════════ -->
<section id="music" class="section">
	<div class="section-inner">
		<Heading title="Releases" />
		<div class="releases-grid">
			{#each artist.releases as release, i (i)}
				<Song
					image={release.image}
					title={release.title}
					year={release.year}
					spotify={release.spotify}
					apple={release.apple}
					amazon={release.amazon}
					youtube={release.youtube}
				/>
			{/each}
		</div>
	</div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════ -->
<!-- VIDEOS                                                                 -->
<!-- ═══════════════════════════════════════════════════════════════════════ -->
<section id="videos" class="section section-parallax" style="background-image: url({artist.videoBg})">
	<div class="parallax-overlay"></div>
	<div class="section-inner section-inner--relative">
		<Heading title="Videos" />
		<div class="videos-grid">
			{#each artist.videos as video (video.embedId)}
				<div class="video-frame">
					<iframe
						src="https://www.youtube.com/embed/{video.embedId}?controls=1"
						title={video.title}
						allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
						allowfullscreen
					></iframe>
				</div>
			{/each}
		</div>
	</div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════ -->
<!-- ABOUT                                                                  -->
<!-- ═══════════════════════════════════════════════════════════════════════ -->
<section id="about" class="section">
	<div class="section-inner section-inner--narrow">
		<Heading title="About" />
		<div class="bio">
			{#each artist.bio as paragraph, i (i)}
				<p>{paragraph}</p>
			{/each}
		</div>
	</div>
</section>

<!-- ═══════════════════════════════════════════════════════════════════════ -->
<!-- BOOKINGS                                                               -->
<!-- ═══════════════════════════════════════════════════════════════════════ -->
<section id="bookings" class="section section-bookings">
	<div class="section-inner">
		<Heading title="Bookings" />
		<a href="mailto:{artist.bookingEmail}" class="booking-email">
			{artist.bookingEmail}
		</a>
		<div class="socials">
			{#if artist.social.instagram}
				<a target="_blank" rel="noopener" href={artist.social.instagram} class="social-link">
					<img src="/images/icons/instagram.png" alt="Instagram" />
				</a>
			{/if}
			{#if artist.social.youtube}
				<a target="_blank" rel="noopener" href={artist.social.youtube} class="social-link">
					<img src="/images/icons/youtube.png" alt="YouTube" />
				</a>
			{/if}
			{#if artist.social.spotify}
				<a target="_blank" rel="noopener" href={artist.social.spotify} class="social-link">
					<img src="/images/icons/spotify-256.png" alt="Spotify" />
				</a>
			{/if}
			{#if artist.social.appleMusic}
				<a target="_blank" rel="noopener" href={artist.social.appleMusic} class="social-link">
					<img src="/images/icons/apple-music.png" alt="Apple Music" />
				</a>
			{/if}
		</div>
	</div>

	<footer class="site-footer">
		<p>© {new Date().getFullYear()} {artist.name}. All rights reserved.</p>
	</footer>
</section>

<style>
	/* ─── Hero ──────────────────────────────────────────────────────────── */
	#hero {
		position: relative;
		min-height: 100vh;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		background-size: cover;
		background-position: center;
		background-repeat: no-repeat;
		overflow: hidden;
	}

	.hero-overlay {
		position: absolute;
		inset: 0;
		background: linear-gradient(
			to bottom,
			rgba(0, 0, 0, 0.4) 0%,
			rgba(0, 0, 0, 0.15) 35%,
			rgba(0, 0, 0, 0.65) 80%,
			rgba(8, 8, 8, 1) 100%
		);
	}

	.hero-logo-wrap {
		position: absolute;
		top: 5.5rem;
		left: 50%;
		transform: translateX(-50%);
		z-index: 2;
	}

	.hero-logo {
		height: 3rem;
		width: auto;
	}

	.hero-content {
		position: relative;
		z-index: 2;
		text-align: center;
		padding: 0 1.5rem;
		pointer-events: none;
	}

	.hero-genre {
		font-family: 'Montserrat', sans-serif;
		font-size: 0.62rem;
		font-weight: 700;
		letter-spacing: 0.32em;
		color: #00d4ff;
		text-transform: uppercase;
		margin: 0 0 0.9rem;
	}

	.hero-name {
		font-family: 'Bebas Neue', cursive;
		font-size: clamp(4rem, 13vw, 9.5rem);
		line-height: 0.88;
		color: white;
		margin: 0;
		letter-spacing: 0.04em;
	}

	.hero-tagline {
		font-family: 'Montserrat', sans-serif;
		font-size: 0.68rem;
		font-weight: 400;
		letter-spacing: 0.3em;
		color: rgba(255, 255, 255, 0.5);
		margin: 1.1rem 0 0;
	}

	.scroll-hint {
		position: absolute;
		bottom: 2.5rem;
		left: 50%;
		transform: translateX(-50%);
		z-index: 2;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 0.5rem;
		animation: float 2.2s ease-in-out infinite;
	}

	.scroll-line {
		display: block;
		width: 1px;
		height: 38px;
		background: linear-gradient(to bottom, transparent, rgba(255, 255, 255, 0.5));
	}

	.scroll-text {
		font-family: 'Montserrat', sans-serif;
		font-size: 0.52rem;
		letter-spacing: 0.28em;
		color: rgba(255, 255, 255, 0.4);
		text-transform: uppercase;
	}

	@keyframes float {
		0%,
		100% {
			transform: translateX(-50%) translateY(0);
		}
		50% {
			transform: translateX(-50%) translateY(9px);
		}
	}

	/* ─── Sections ──────────────────────────────────────────────────────── */
	.section {
		background-color: #080808;
		padding: 6rem 0;
	}

	.section-parallax {
		position: relative;
		background-color: transparent;
		background-size: cover;
		background-position: center;
		background-attachment: fixed;
	}

	.parallax-overlay {
		position: absolute;
		inset: 0;
		background: rgba(0, 0, 0, 0.78);
	}

	.section-inner {
		max-width: 1200px;
		margin: 0 auto;
		padding: 0 1.5rem;
	}

	.section-inner--relative {
		position: relative;
		z-index: 1;
	}

	.section-inner--narrow {
		max-width: 760px;
	}

	/* ─── Releases grid ──────────────────────────────────────────────────── */
	.releases-grid {
		display: grid;
		grid-template-columns: repeat(2, 1fr);
		gap: 1rem;
		margin-top: 3rem;
	}

	@media (min-width: 540px) {
		.releases-grid {
			grid-template-columns: repeat(3, 1fr);
			gap: 1.25rem;
		}
	}

	@media (min-width: 900px) {
		.releases-grid {
			grid-template-columns: repeat(4, 1fr);
			gap: 1.75rem;
		}
	}

	@media (min-width: 1200px) {
		.releases-grid {
			grid-template-columns: repeat(6, 1fr);
			gap: 1.5rem;
		}
	}

	/* ─── Videos ─────────────────────────────────────────────────────────── */
	.videos-grid {
		margin-top: 3rem;
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(min(100%, 560px), 1fr));
		gap: 1.5rem;
		justify-items: center;
	}

	.video-frame {
		width: 100%;
		max-width: 700px;
		aspect-ratio: 16 / 9;
	}

	.video-frame iframe {
		width: 100%;
		height: 100%;
		border-radius: 6px;
		display: block;
	}

	/* ─── Bio ────────────────────────────────────────────────────────────── */
	.bio {
		margin-top: 2.5rem;
		text-align: center;
	}

	.bio p {
		font-family: 'Montserrat', sans-serif;
		font-size: 0.95rem;
		font-weight: 400;
		line-height: 1.95;
		color: rgba(255, 255, 255, 0.65);
		margin-bottom: 1.25rem;
	}

	/* ─── Bookings ───────────────────────────────────────────────────────── */
	.section-bookings {
		padding-bottom: 0;
	}

	.booking-email {
		display: block;
		font-family: 'Montserrat', sans-serif;
		font-size: clamp(0.8rem, 2.2vw, 1.2rem);
		font-weight: 600;
		letter-spacing: 0.06em;
		color: white;
		text-decoration: none;
		text-align: center;
		margin-top: 2rem;
		transition: color 0.2s;
	}

	.booking-email:hover {
		color: #00d4ff;
	}

	.socials {
		display: flex;
		justify-content: center;
		gap: 1.75rem;
		margin-top: 3rem;
		padding-bottom: 5rem;
	}

	.social-link img {
		width: 2.2rem;
		height: 2.2rem;
		object-fit: contain;
		opacity: 0.7;
		transition:
			opacity 0.2s,
			transform 0.2s;
	}

	.social-link:hover img {
		opacity: 1;
		transform: scale(1.18);
	}

	/* ─── Footer ─────────────────────────────────────────────────────────── */
	.site-footer {
		border-top: 1px solid rgba(255, 255, 255, 0.07);
		padding: 1.5rem;
		text-align: center;
	}

	.site-footer p {
		font-family: 'Montserrat', sans-serif;
		font-size: 0.65rem;
		letter-spacing: 0.12em;
		color: rgba(255, 255, 255, 0.2);
		margin: 0;
	}
</style>
