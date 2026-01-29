<script>
	import JSPlayground from '$lib/components/JSPlayground.svelte';
</script>

<svelte:head>
	<title>Playground - Statue</title>
</svelte:head>

<div class="playground-window-container">
	<div class="window-wrapper">
		<div class="window-header">
			<h1>Interactive Playground</h1>
			<p>Run JavaScript code directly in your browser.</p>
		</div>
		
		<div class="window-content">
			<JSPlayground />
		</div>
	</div>
</div>

<style>
	.playground-window-container {
		min-height: 100vh;
		width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 80px 20px 40px; 
		background-color: var(--color-bg-2, #f5f5f5);
		box-sizing: border-box;
	}

	.window-wrapper {
		width: 100%;
		max-width: 900px;
		background: var(--color-bg, #ffffff);
		border-radius: 12px;
		box-shadow: 0 20px 40px -10px rgba(0, 0, 0, 0.15);
		border: 1px solid var(--color-border, #e5e5e5);
		overflow: hidden;
	}

	.window-header {
		padding: 2rem 2rem 1rem;
		text-align: center;
		border-bottom: 1px solid var(--color-border, #f0f0f0);
	}

	.window-header h1 {
		margin: 0 0 0.5rem 0;
		font-size: 1.8rem;
		color: var(--color-heading, #111);
	}

	.window-header p {
		margin: 0;
		color: var(--color-text-muted, #666);
	}

	.window-content {
		padding: 0; 
	}

	.window-content :global(.playground) {
		margin: 0 !important;
		border: none !important;
		border-radius: 0 !important;
		height: 600px;
	}
</style>
