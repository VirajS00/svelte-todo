<script>
	import TodoItems from './TodoItems.svelte';
	import AddTodo from './AddTodo.svelte';

	let dummyItems = [
        {
			id: 1,
            name: 'Hello',
            done: false
        },
		{
			id: 2,
			name: 'Go to the gym',
			done: true
		},
		{
			id: 3,
			name: 'Leave home at 2am',
			done: false
		},
    ]
</script>

<main>
	<div class="todo-container">
		<h1>Todo List</h1>
		<TodoItems todoItems={dummyItems} />
		<AddTodo bind:todoItems={dummyItems} />
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