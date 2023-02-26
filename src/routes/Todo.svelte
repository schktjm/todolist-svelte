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

<li class="wrapper">
	<label class="todo-label">
		{#if isChecked}
			<img src={checked} alt="" />
		{:else}
			<img src={noChecked} alt="" />
		{/if}
		<input {id} class="checkbox" type="checkbox" bind:checked={isChecked} on:change={onChange} />
		<div class="text">
			{text}
		</div>
	</label>
</li>

<style lang="scss">
	.wrapper {
		list-style: none;
		font-size: 16px;
		border-top: 1px dotted var(--color-gray-1);

		&:last-child {
			border-bottom: 1px dotted var(--color-gray-1);
		}

		input[type='checkbox'] {
			visibility: hidden;
		}

		.todo-label {
			display: flex;
			align-items: center;
			min-height: 28px;
			cursor: pointer;
			padding: 0.25rem 0;

			.checkbox {
				&:checked + .text {
					color: var(--color-gray-0);
				}
			}

			.text {
				width: 300px;
				overflow-wrap: break-word;
			}
		}
	}
</style>
