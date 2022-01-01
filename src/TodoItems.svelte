<script>
    export let todoItems;
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
        position: relative;
        overflow: hidden;
        display: flex;
        flex-shrink: 0;
        gap: .5em;
        padding: 1em 2em;
        /* border: .1em solid rgb(0, 80, 177); */
        background-color: rgb(219, 236, 255);
        border-radius: 100vh;
        align-items: center;
        font-size: 1.2rem;
        transition: background-color 250ms ease;
    }

    .todo-check {
        display: none;
    }

    .done {
        background-color: rgb(59, 252, 130);
    }

    .todo-container::after {
        content: '';
        position: absolute;
        top: 51%;
        transform-origin: left;
        transform: scale(0,1);
        background-color: rgb(0, 62, 0);
        height: .15em;
        left: 2em;
        right: 2em;
        transition: transform 250ms ease;
    }

    .done::after {
        transform: scale(1,1);
    }
</style>

<div class="all-todos">
    {#each todoItems as {id, name, done}}
        <label for="{id}" class="todo-container {done?'done':''}">
            <input type="checkbox" id="{id}" bind:checked={done} class="todo-check">
            {name}
        </label>
    {/each}
</div>