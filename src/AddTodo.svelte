<script>
    export let todoItems;

    let todoName = '';

    function addTodo() {
        let lastId = todoItems.length === 0 ? 0 : todoItems[todoItems.length - 1].id;

        let newId = parseInt(lastId) + 1;

        todoItems.push({
            id: newId,
			name: todoName,
			done: false
        });

        todoItems = todoItems;
        todoName = '';
    }

    const clearTodos = () => todoItems = todoItems.filter(x => !x.done);
</script>

<style>
    form {
        display: flex;
        width: 100%;
        gap: .5em;
        margin-top: 1em;
    }

    form > * {
        flex-grow: 1;
    }

    .text-box {
        border-radius: 100vh;
        border: 1px solid #ccc;
        padding: .5em 1em;
    }

    .button {
        border-radius: 100vh;
        border: 0;
        background-color: rgb(0, 96, 198);
        color: #fff;
        transition: background-color 250ms ease;
    }

    .button:hover {
        background-color: rgb(0, 73, 152);
    }

    .clear {
        background-color: rgb(136, 0, 0);
    }

    .clear:hover {
        background-color:rgb(99, 0, 0);
    }
</style>

<form on:submit|preventDefault={addTodo}>
    <input type="text" placeholder="Enter ToDo name" class="text-box" bind:value={todoName}>
    <input type="submit" value="Add Todo" class="button">
    <input type="button" value="Clear" class="button clear" on:click={clearTodos}>
</form>