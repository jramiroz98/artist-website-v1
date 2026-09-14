<script lang="ts">
	let { title = 'Title' }: { title: string } = $props();
</script>

<header class="section-heading">
	<div class="accent"></div>
	<h2>{title.toUpperCase()}</h2>
</header>

<style>
	.section-heading {
		text-align: center;
	}

	.accent {
		width: 36px;
		height: 3px;
		background: #00d4ff;
		margin: 0 auto 1.1rem;
		border-radius: 2px;
	}

	h2 {
		font-family: 'Bebas Neue', cursive;
		font-size: clamp(2.5rem, 6vw, 4rem);
		color: white;
		margin: 0;
		letter-spacing: 0.08em;
		line-height: 1;
	}
</style>
