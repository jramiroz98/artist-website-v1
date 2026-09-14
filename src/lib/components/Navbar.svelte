<script lang="ts">
	import { artist } from '$lib/artist.config';

	let scrolled = $state(false);
	let menuOpen = $state(false);

	$effect(() => {
		const onScroll = () => {
			scrolled = window.scrollY > 60;
		};
		window.addEventListener('scroll', onScroll, { passive: true });
		return () => window.removeEventListener('scroll', onScroll);
	});

	const links = [
		{ label: 'Music', href: '#music' },
		{ label: 'Videos', href: '#videos' },
		{ label: 'About', href: '#about' },
		{ label: 'Bookings', href: '#bookings' }
	];
</script>

<nav class:scrolled>
	<a class="logo-link" href="/">
		<img src={artist.logo} alt={artist.name} class="logo" />
	</a>

	<ul class="links">
		{#each links as link}
			<li><a href={link.href}>{link.label}</a></li>
		{/each}
	</ul>

	<button class="burger" aria-label="Toggle menu" onclick={() => (menuOpen = !menuOpen)}>
		<span></span>
		<span></span>
		<span></span>
	</button>
</nav>

{#if menuOpen}
	<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_static_element_interactions -->
	<div class="mobile-overlay" role="dialog" aria-modal="true" tabindex="-1" onclick={() => (menuOpen = false)}>
		{#each links as link}
			<a href={link.href} onclick={() => (menuOpen = false)}>{link.label}</a>
		{/each}
	</div>
{/if}

<style>
	nav {
		position: fixed;
		inset: 0 0 auto 0;
		z-index: 200;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 1.5rem 2.5rem;
		transition:
			background 0.3s ease,
			padding 0.3s ease,
			border-color 0.3s ease;
		border-bottom: 1px solid transparent;
	}

	nav.scrolled {
		background: rgba(8, 8, 8, 0.92);
		backdrop-filter: blur(16px);
		-webkit-backdrop-filter: blur(16px);
		padding: 0.9rem 2.5rem;
		border-bottom-color: rgba(255, 255, 255, 0.07);
	}

	.logo {
		height: 2rem;
		width: auto;
	}

	.links {
		display: none;
		list-style: none;
		margin: 0;
		padding: 0;
		gap: 2.5rem;
	}

	.links a {
		color: rgba(255, 255, 255, 0.65);
		text-decoration: none;
		font-family: 'Montserrat', sans-serif;
		font-size: 0.68rem;
		font-weight: 700;
		letter-spacing: 0.2em;
		text-transform: uppercase;
		transition: color 0.2s;
	}

	.links a:hover {
		color: #ffffff;
	}

	.burger {
		display: flex;
		flex-direction: column;
		gap: 5px;
		background: none;
		border: none;
		cursor: pointer;
		padding: 4px;
	}

	.burger span {
		display: block;
		width: 22px;
		height: 2px;
		background: white;
		border-radius: 2px;
	}

	/* ─── Mobile overlay menu ──────────────────────────────────────────── */
	.mobile-overlay {
		position: fixed;
		inset: 0;
		background: rgba(6, 6, 6, 0.97);
		z-index: 199;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		gap: 2.5rem;
	}

	.mobile-overlay a {
		color: white;
		text-decoration: none;
		font-family: 'Bebas Neue', cursive;
		font-size: 3.5rem;
		letter-spacing: 0.08em;
		transition: color 0.2s;
	}

	.mobile-overlay a:hover {
		color: #00d4ff;
	}

	@media (min-width: 768px) {
		.links {
			display: flex;
		}
		.burger {
			display: none;
		}
	}
</style>
