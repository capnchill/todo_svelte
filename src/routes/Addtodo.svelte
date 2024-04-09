<script>
	import { createEventDispatcher } from 'svelte';

	let task = '';
	const dispatch = createEventDispatcher();

	function addTodo() {
		if (!(task === undefined || task === null || task === '')) {
			dispatch('submit', { task });
			task = '';
		} else {
			throw new Error('task is undefined');
		}
	}
</script>

<form class="flex flex-col" on:submit|preventDefault={addTodo}>
	<input type="text" class="border-2 border-black p-4" bind:value={task} />
	<button class="mt-2 bg-gray-600 p-2 text-gray-300">Add</button>
</form>
