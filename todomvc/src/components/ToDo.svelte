<script>
    export let todo;
    export let removeTodo;
    export let completeTodo;
</script>

<main class="todo">
    <div class="todo-item">
        <input
            on:change={() => completeTodo(todo.id)}
            bind:checked={todo.completed}
            id="todo"
            type="checkbox"
            class="checkbox-round"
        />

        <span class:completed={todo.completed}>
            <input
                placeholder="Deleted todo"
                bind:value={todo.text}
                type="text"
                disabled={todo.completed}
            />
        </span>

        <button
            aria-label="Remove todo"
            on:click={() => removeTodo(todo.id)}
            class="remove"
        />
    </div>
</main>

<style>
    :root {
        --x-color: rgb(91, 123, 170); /* changes the color of the remove button, ex rgb(103, 103, 103); */
        --x-highlight:  rgb(0, 0, 170);/* changes the color of the remove button when hovered, ex rgb(108, 38, 38); */
        --checkbox-color:  rgb(200, 200, 170);/* changes the color of the checkbox, ex rgb(108, 38, 38); */
        --font-size: 24px; /* changes the height of the line and general spacing, ex 24px; */
        --line-height: calc(var(--font-size) * 3); /* dependent on the font-size */
    }
    /**
        Styles for entire todo component, to make sure everything stays inline
    **/
    .todo {
        border-top: 1px solid var(--color-outline);
        box-shadow: 0 0 4px var(--color-shadow);
    }
    .todo-item {
        position: relative;
        display: flex;
        align-items: center;
    }
    /**
        Todo text box
    **/
    input[type="text"] {
        font-family: inherit;
        font-weight: 300;
        font-size: var(--font-size);
        line-height: var(--line-height);
        background-color: var(--color-bg);
        color: var(--color-text);
        border: none;
        width: 90%;
        margin-left: calc(var(--font-size) * 4);
    }
    input[type="text"]:focus {
        outline: none;
    }
    input[type="text"]:disabled {
        text-decoration: line-through;
        color: var(--x-color);
    }

    /**
        Remove button
    **/
    .remove {
        display: none;
        position: absolute;
        right: var(--font-size);
        background-color: var(--color-bg);
        font-size: calc(var(--font-size) * 2);
        color: var(--x-color);
        transition: color 0.2s ease-out;
        border: none;
    }
    .remove:hover {
        color: var(--x-highlight);
    }
    .remove:after {
        content: "clear";
    }
    .todo:hover .remove {
        display: block;
    }

</style>
