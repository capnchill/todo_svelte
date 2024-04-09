<script>
	import Addtodo from './Addtodo.svelte';
	import Todo from './Todo.svelte';
	import Filterbutton from './Filterbutton.svelte';
	import Bulkaction from './Bulkaction.svelte';
	import { generateRandomId } from './utils.js';

	let todos = [];
	let all = true;
	let active = false;
	let completed = false;

	function addTodo(event) {
		let todo = {
			id: generateRandomId(),
			task: event.detail.task,
			completed: false
		};

		todos = [todo, ...todos];

		console.log(todos);
	}

	function deleteTodo(event) {
		let id = event.detail.id;
		let index = todos.findIndex((todo) => todo.id === id);
		todos.splice(id, 1);
		todos = todos;
	}

	function toggleCheck() {
		if (todos.filter((todo) => todo.completed === false).length !== 0) {
			todos.forEach((todo) => (todo.completed = true));
			todos = todos;
		} else if (todos.filter((todo) => todo.completed === true).length !== 0) {
			todos.forEach((todo) => (todo.completed = false));
			todos = todos;
		}
	}

	function removeCompleted() {
		let active = todos.filter((todo) => todo.completed === false);
		todos = active;
		console.log(active);
	}

	function clickAll() {
		all = true;
		active = false;
		completed = false;
	}

	let activeTodos = [];
	function clickActive() {
		all = false;
		active = true;
		completed = false;

		activeTodos = todos.filter((todo) => todo.completed === false);
	}

	let completedTodos = [];
	function clickCompleted() {
		all = false;
		active = false;
		completed = true;

		completedTodos = todos.filter((todo) => todo.completed === true);
	}
</script>

<div class="mx-auto mb-4">
	<h3>What needs to be done?</h3>
</div>

<div class="mb-4">
	<Addtodo on:submit={addTodo} />
</div>

{#if todos.length > 0}
	<div class="mx-auto mb-4">
		<Filterbutton
			on:clickAll={clickAll}
			on:clickActive={clickActive}
			on:clickCompleted={clickCompleted}
		/>
	</div>

	<div class="mx-auto w-4/5">
		{#if all}
			{#each todos as todo (todo.id)}
				<Todo {todo} on:click={deleteTodo} />
			{/each}
		{/if}

		{#if active}
			{#each activeTodos as todo (todo.id)}
				<Todo {todo} on:click={deleteTodo} />
			{/each}
		{/if}

		{#if completed}
			{#each completedTodos as todo (todo.id)}
				<Todo {todo} on:click={deleteTodo} />
			{/each}
		{/if}
	</div>

	<div class="border-[1px] border-slate-400"></div>

	<Bulkaction on:CheckAll={toggleCheck} on:removeCompleted={removeCompleted} />
{/if}
