<script>
	import { createEventDispatcher } from 'svelte';

	let editMode = false;
	export let todo;

	let dispatch = createEventDispatcher();

	function deleteTodo(id) {
		// console.log('Attempting to dispatch click event');
		dispatch('click', { id });
	}

	function editTodo() {
		editMode = true;
	}

	let updatedTodo = '';
	function saveEdit(id) {
		console.log(id);
		console.log(updatedTodo);
		editMode = false;
		dispatch('clickEdit', { id, updatedTodo });
	}
</script>

<div class="mb-4">
	<div class="mb-4">
		{#if editMode}
			<!-- Input Group -->
			<div class="mb-4">
				<form on:submit={() => saveEdit(todo.id)}>
					<p class="mb-2">Update Task Name</p>
					<input
						type="text"
						bind:value={updatedTodo}
						class="w-full rounded border border-gray-300 px-2 py-1"
					/>
				</form>
			</div>
		{:else}
			<!-- Checkbox Group -->
			<div class="mb-4">
				<div class="flex items-center">
					<input type="checkbox" class="h-10 w-10" bind:checked={todo.completed} />
					<label for="checkbox" class="pl-4">{todo.task}</label>
				</div>
			</div>

			<div class="flex gap-2">
				<button
					class="mt-10 flex-1 border-2 border-slate-400 bg-white px-4 text-lg text-black hover:underline focus:outline-none sm:mt-0"
					on:click={editTodo}
				>
					Edit
				</button>

				<button
					class="mt-10 flex-1 border-2 border-slate-400 bg-white px-4 text-lg text-black hover:underline focus:outline-none sm:mt-0"
					on:click={() => deleteTodo(todo.id)}
				>
					Delete
				</button>
			</div>
		{/if}
	</div>
</div>
