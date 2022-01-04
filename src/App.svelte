<script>
	import TodoItems from './TodoItems.svelte';
	import AddTodo from './AddTodo.svelte';

	let scroll;

	let todoItems = (localStorage.getItem("username") === null) ? [] : JSON.parse(localStorage.getItem("todos"));

	$: localStorage.setItem("todos", JSON.stringify(todoItems));

	function handleScroll(event) {
		scroll = event.detail.text;
	}

</script>

<main>
	<div class="todo-container">
		<h1>Todo List</h1>
		<TodoItems todoItems={todoItems} scroll={scroll} />
		<AddTodo bind:todoItems={todoItems} on:scroll={handleScroll} />
	</div>
</main>

<style>
	main {
		min-height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
	}
	.todo-container {
		border: .2em solid rgb(0, 58, 130);
		width: 90%;
		max-width: 450px;
		min-height: 500px;
		padding: 1em;
		border-radius: 1em;
	}

	h1 {
		text-align: center;
		border-bottom: .1em solid #eee;
		padding-bottom: .3em;
	}
</style>