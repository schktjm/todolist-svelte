<script>
	import './styles.css';
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="true" />
	<link href="https://fonts.googleapis.com/css2?family=Jua&display=swap" rel="stylesheet" />
</svelte:head>

<div class="app">
	<main>
		<slot />
	</main>
</div>

<style>
	main {
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
	}
</style>
