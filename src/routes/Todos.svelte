<script>
	import Addtodo from './Addtodo.svelte';
	import Todo from './Todo.svelte';
	import Filterbutton from './Filterbutton.svelte';
	import Bulkaction from './Bulkaction.svelte';
</script>

<div class="mx-auto mb-4">
	<h3>What needs to be done?</h3>
</div>

<div class="mb-4">
	<Addtodo />
</div>

<div class="mx-auto mb-4">
	<Filterbutton />
</div>

<div class="mx-auto w-4/5">
	<Todo />
</div>

<div class="border-[1px] border-slate-400"></div>

<Bulkaction />
