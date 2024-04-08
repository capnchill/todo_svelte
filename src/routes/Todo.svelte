<script>
	let editMode = false;
	export let todo;
</script>

<div class="mb-4">
	<div class="mb-4">
		{#if editMode}
			<!-- Input Group -->
			<div class="block">
				<span>New Name for Create Your first App</span>
				<input type="text" value="Hey" class="rounded border border-gray-300 px-2 py-1" />
			</div>
		{:else}
			<!-- Checkbox Group -->
			<div class="flex items-center">
				<input type="checkbox" class="h-10 w-10" bind:checked={todo.completed} />
				<label for="checkbox" class="pl-4">{todo.task}</label>
			</div>
		{/if}
	</div>

	<div class="flex gap-2">
		<button
			class="mt-10 flex-1 border-2 border-slate-400 bg-white px-4 text-lg text-black hover:underline focus:outline-none sm:mt-0"
		>
			Edit
		</button>

		<button
			class="mt-10 flex-1 border-2 border-slate-400 bg-white px-4 text-lg text-black hover:underline focus:outline-none sm:mt-0"
		>
			Delete
		</button>
	</div>
</div>
