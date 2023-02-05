<script lang="ts">
	import type { Todo } from './type';

	export let status: Todo['status'];
	export let text: Todo['text'];
</script>

<div>
	<input type="checkbox" checked={status === 'done'} />
	{text}
</div>
