<script>
	import { createEventDispatcher } from 'svelte';

	let dispatch = createEventDispatcher();

	function clickCheckAll() {
		dispatch('CheckAll');
	}

	function clickRemoveCompleted() {
		dispatch('removeCompleted');
	}
</script>

<div class="mt-4">
	<div class="flex gap-2">
		<button
			class="mt-10 flex-1 bg-black py-1 text-lg font-extralight text-white hover:underline focus:outline-none sm:mt-0"
			on:click={clickCheckAll}
		>
			Check All
		</button>
		<button
			class="mt-10 flex-1 bg-black py-1 text-lg font-extralight text-white hover:underline focus:outline-none sm:mt-0"
			on:click={clickRemoveCompleted}
		>
			Remove Completed
		</button>
	</div>
</div>
