<script>
	import { createEventDispatcher } from 'svelte';

	let dispatch = createEventDispatcher();

	function clickAllFilter() {
		dispatch('clickAll');
	}

	function clickActiveFilter() {
		dispatch('clickActive');
	}

	function clickCompletedFilter() {
		dispatch('clickCompleted');
	}
</script>

<div class="mx-auto">
	<button
		class="active:underlined mt-10 border-2 border-slate-400 bg-white px-4 text-lg text-black hover:underline focus:outline-none sm:mt-0"
		on:click={clickAllFilter}>All</button
	>
	<button
		class="mt-10 border-2 border-slate-400 bg-white px-4 text-lg text-black hover:underline focus:outline-none sm:mt-0"
		on:click={clickActiveFilter}>Active</button
	>
	<button
		class="mt-10 border-2 border-slate-400 bg-white px-4 text-lg text-black hover:underline focus:outline-none sm:mt-0"
		on:click={clickCompletedFilter}>Completed</button
	>
</div>
