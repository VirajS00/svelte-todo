<script>
    export let todoItems;
    
    function changeState() {
        console.log(todoItems)
    }
</script>

<style>
    .all-todos {
        display: flex;
        flex-direction: column;
        gap: 1em;
        overflow-y: scroll;
        height: 250px;
    }

    .todo-container {
        display: flex;
        gap: .5em;
        padding: 1em 2em;
        border: .1em solid rgb(0, 80, 177);
        border-radius: 100vh;
        align-items: center;
    }
</style>

<div class="all-todos">
    {#each todoItems as {id, name, done}}
    <label for="{id}" class="todo-container">
        <input type="checkbox" id="{id}" bind:checked={done} class={done ? 'done' : ''} on:change={changeState}>
        {name}
    </label>
    {/each}
</div>