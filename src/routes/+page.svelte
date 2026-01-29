<script>
	import { Hero, Stats, Categories, LatestContent, BuiltBy } from 'statue-ssg';

	const { data } = $props();
</script>

<svelte:head>
	<title>Statue</title>
	<meta
		name="description"
		content="Statue SSG powered by Svelte, generates static sites from markdown content."
	/>
</svelte:head>

<div
	class="min-h-screen bg-linear-to-b from-(--color-hero-from) via-(--color-hero-via) to-(--color-hero-to)"
>
	<Hero />

	<div class="playground-cta">
		<a href="/playground" class="playground-button">
			<span class="icon">▶</span>
			Try the JS Playground
		</a>
		<p class="cta-text">Run code directly in your browser</p>
	</div>


	<section class="typewriter-showcase">
		<BuiltBy />
	</section>

	<div class="stats-wrapper">
		<Stats />
	</div>

	<div class="container mx-auto px-4 py-10">
		<Categories directories={data.directories} />

		<LatestContent rootContent={data.rootContent} />
	</div>
</div>

<style>
	/* Add smooth scroll behavior */
	:global(html) {
		scroll-behavior: smooth;
	}

	/* Reduce padding of Stats component on this page to sit closer to BuiltBy */
	.stats-wrapper :global(.container) {
		padding-top: 1rem !important;
	}

	/* Typewriter Showcase Section */
	.typewriter-showcase {
		max-width: 1200px;
		margin: 0 auto;
		padding: 1rem 2rem 0;
		text-align: center;
		position: relative;
		z-index: 10;
	}

	/* Playground */
	.playground-cta {
		text-align: center;
		padding: 2rem 1rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1rem;
	}

	.playground-button {
		display: inline-flex;
		align-items: center;
		gap: 0.5rem;
		background-color: #cc0000; 
		color: white;
		padding: 12px 24px;
		border-radius: 9999px;
		font-weight: 600;
		text-decoration: none;
		transition: transform 0.2s, box-shadow 0.2s;
		box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
	}

	.playground-button:hover {
		transform: translateY(-2px);
		box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.2);
		background-color: #b30000;
	}

	.cta-text {
		color: var(--color-text-muted, #666);
		font-size: 0.9rem;
		margin: 0;
	}
</style>
