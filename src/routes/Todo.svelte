<script lang="ts">
	import type { Todo } from './type';
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	function onChange() {
		dispatch('change', {
			id,
			text,
			status: isChecked ? 'done' : 'todo'
		});
	}

	import checked from '$lib/images/checked.svg';
	import noChecked from '$lib/images/not-checked.svg';

	export let status: Todo['status'];
	export let text: Todo['text'];
	export let id: Todo['id'];

	$: isChecked = status === 'done';
</script>

<div class="wrapper">
	<label>
		{#if isChecked}
			<img src={checked} alt="" />
		{:else}
			<img src={noChecked} alt="" />
		{/if}
		<input {id} class="checkbox" type="checkbox" bind:checked={isChecked} on:change={onChange} />
		<span class="text">
			{text}
		</span>
	</label>
</div>

<style lang="scss">
	.wrapper {
		input[type='checkbox'] {
			visibility: hidden;
		}
	}
</style>
