<script lang="ts">
	import Modal from '$lib/components/Modal.svelte';

	let {
		image,
		title,
		year = '',
		spotify = '',
		apple = '',
		amazon = '',
		youtube = ''
	}: {
		image: string;
		title: string;
		year?: string;
		spotify?: string;
		apple?: string;
		amazon?: string;
		youtube?: string;
	} = $props();

	let showModal = $state(false);
</script>

<button class="card" onclick={() => (showModal = true)}>
	<div class="art-wrap">
		<img src={image} alt={title} class="art" />
		<div class="overlay">
			<span class="listen-label">LISTEN</span>
		</div>
	</div>
	<div class="card-info">
		<span class="card-title">{title.toUpperCase()}</span>
		{#if year}<span class="card-year">{year}</span>{/if}
	</div>
</button>

<Modal bind:showModal>
	<!-- Edge-to-edge album art at top of modal -->
	<div class="modal-art-wrap">
		<img src={image} alt={title} class="modal-art" />
	</div>
	<!-- Info + platform buttons with padding -->
	<div class="modal-info">
		<h3 class="modal-title">{title.toUpperCase()}</h3>
		{#if year}<p class="modal-year">{year}</p>{/if}
		<div class="platforms">
			{#if spotify}
				<a target="_blank" rel="noopener" href={spotify} class="platform-btn spotify">
					<img src="/images/icons/spotify-256.png" alt="" />
					<span>Spotify</span>
				</a>
			{/if}
			{#if apple}
				<a target="_blank" rel="noopener" href={apple} class="platform-btn apple">
					<img src="/images/icons/apple-music.png" alt="" />
					<span>Apple Music</span>
				</a>
			{/if}
			{#if amazon}
				<a target="_blank" rel="noopener" href={amazon} class="platform-btn amazon">
					<img src="/images/icons/amazon.png" alt="" />
					<span>Amazon Music</span>
				</a>
			{/if}
			{#if youtube}
				<a target="_blank" rel="noopener" href={youtube} class="platform-btn yt">
					<img src="/images/icons/youtube.png" alt="" />
					<span>YouTube</span>
				</a>
			{/if}
		</div>
	</div>
</Modal>

<style>
	/* ─── Card ─────────────────────────────────────────────────────────── */
	.card {
		cursor: pointer;
		background: none;
		border: none;
		padding: 0;
		text-align: left;
		width: 100%;
	}

	.art-wrap {
		position: relative;
		aspect-ratio: 1;
		border-radius: 6px;
		overflow: hidden;
	}

	.art {
		width: 100%;
		height: 100%;
		object-fit: cover;
		display: block;
		transition: transform 0.35s ease;
	}

	.overlay {
		position: absolute;
		inset: 0;
		background: rgba(0, 0, 0, 0.55);
		display: flex;
		align-items: center;
		justify-content: center;
		opacity: 0;
		transition: opacity 0.25s;
	}

	.listen-label {
		font-family: 'Montserrat', sans-serif;
		font-size: 0.6rem;
		font-weight: 700;
		letter-spacing: 0.22em;
		color: white;
		border: 1px solid rgba(255, 255, 255, 0.65);
		padding: 0.45rem 0.9rem;
		border-radius: 2px;
	}

	.card:hover .art {
		transform: scale(1.06);
	}

	.card:hover .overlay {
		opacity: 1;
	}

	.card-info {
		padding: 0.55rem 0.15rem 0;
	}

	.card-title {
		display: block;
		font-family: 'Montserrat', sans-serif;
		font-size: 0.68rem;
		font-weight: 700;
		letter-spacing: 0.1em;
		color: white;
	}

	.card-year {
		display: block;
		font-family: 'Montserrat', sans-serif;
		font-size: 0.62rem;
		color: rgba(255, 255, 255, 0.38);
		margin-top: 0.15rem;
	}

	/* ─── Modal content ─────────────────────────────────────────────────── */
	.modal-art-wrap {
		line-height: 0;
	}

	.modal-art {
		width: 100%;
		aspect-ratio: 1;
		object-fit: cover;
		display: block;
	}

	.modal-info {
		padding: 1.1rem 1.25rem 1.4rem;
	}

	.modal-title {
		font-family: 'Bebas Neue', cursive;
		font-size: 1.9rem;
		letter-spacing: 0.08em;
		color: white;
		margin: 0;
	}

	.modal-year {
		font-family: 'Montserrat', sans-serif;
		font-size: 0.68rem;
		color: rgba(255, 255, 255, 0.38);
		margin: 0.2rem 0 0;
		letter-spacing: 0.1em;
	}

	.platforms {
		display: flex;
		flex-direction: column;
		gap: 0.55rem;
		margin-top: 1.1rem;
	}

	.platform-btn {
		display: flex;
		align-items: center;
		gap: 0.75rem;
		padding: 0.6rem 1rem;
		border-radius: 5px;
		text-decoration: none;
		font-family: 'Montserrat', sans-serif;
		font-size: 0.78rem;
		font-weight: 600;
		color: white;
		letter-spacing: 0.04em;
		transition:
			opacity 0.2s,
			transform 0.15s;
	}

	.platform-btn:hover {
		opacity: 0.85;
		transform: translateX(3px);
	}

	.platform-btn img {
		width: 1.35rem;
		height: 1.35rem;
		object-fit: contain;
		flex-shrink: 0;
	}

	.spotify {
		background: #1db954;
	}
	.apple {
		background: #fc3c44;
	}
	.amazon {
		background: #00a8e1;
	}
	.yt {
		background: #ff0000;
	}
</style>
