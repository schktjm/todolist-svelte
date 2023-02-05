<script lang="ts">
	import Todo from './Todo.svelte';
	import type { Todo as TodoType } from './type';

	const todos: TodoType[] = [
		{
			id: '1',
			status: 'todo',
			text: '風呂掃除'
		},
		{
			id: '2',
			status: 'done',
			text: 'お皿洗い'
		},
		{
			id: '3',
			status: 'done',
			text: '掃除機かけ'
		},
		{
			id: '4',
			status: 'todo',
			text: '洗濯物干す'
		}
	];

	let isHideDone = true;
</script>

<label>
	<input type="checkbox" bind:checked={isHideDone} />
	完了済みの項目を隠す
</label>

<ul>
	{#each todos as todo (todo.id)}
		{#if !(isHideDone && todo.status === 'done')}
			<Todo {...todo} />
		{/if}
	{/each}
</ul>
