<script lang="ts">
	import Todo from './Todo.svelte';
	import type { Todo as TodoType } from './type';

	let todos: TodoType[] = [
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
		},
		{
			id: '5',
			status: 'todo',
			text: 'マイナンバーカードが落ちてないか警察署に行く'
		}
	];

	function handleChange(event: CustomEvent<TodoType>) {
		console.log(event.detail);
		todos = todos.map((todo) => {
			if (todo.id === event.detail.id) {
				return event.detail;
			}
			return todo;
		});
	}

	let isHideDone = false;
</script>

<label>
	<input type="checkbox" bind:checked={isHideDone} />
	完了済みの項目を隠す
</label>

<ul class="todo-list">
	{#each todos as todo (todo.id)}
		{#if !(isHideDone && todo.status === 'done')}
			<Todo {...todo} on:change={handleChange} />
		{/if}
	{/each}
</ul>

<style lang="scss">
	.todo-list {
		padding: 0;
		margin: 0;
		margin-top: 1rem;
	}
</style>
