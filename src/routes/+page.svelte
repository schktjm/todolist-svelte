<script>
	import Todolist from './Todolist.svelte';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<h1>Todolist Svelte</h1>

	<Todolist />
</section>

<style lang="scss">
	h1 {
		font-family: var(--font-title);
	}
</style>
