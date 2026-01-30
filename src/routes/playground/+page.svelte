<script>
	import Playground from '$lib/components/Playground.svelte';
</script>

<svelte:head>
	<title>Playground | Statue</title>
</svelte:head>

<div class="page-wrapper">
	<div class="container mx-auto px-4 py-12">
		
		<div class="header-content text-center mb-8">
			<h1 class="text-4xl font-bold mb-4 text-(--color-heading)">Interactive Playground</h1>
			<p class="text-xl text-(--color-text-muted)">
                Write and run code in your browser!
			</p>
		</div>

		<Playground />

		<div class="text-center mt-12">
			<a href="/" class="back-link">← Back to Home</a>
		</div>
	</div>
</div>

<style>
	.page-wrapper {
		min-height: 100vh;
		background-color: var(--color-bg, #CBC3E3);
        padding-top: 6rem;
	}
	
	.back-link {
		color: var(--color-primary, #666);
		text-decoration: none;
		font-weight: 500;
	}
	.back-link:hover {
		text-decoration: underline;
	}
</style>
