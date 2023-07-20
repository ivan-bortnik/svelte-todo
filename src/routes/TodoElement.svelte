<script>

import { createEventDispatcher } from "svelte";
const dispatch = createEventDispatcher()

export var text
export var done

function removeTodo() {
    dispatch('remove')
}

</script>

<main>

<div class={done ? "task-done" : ""}>

    <input type="checkbox" bind:checked={done}>

    <p>{text}</p>

    <button on:click={removeTodo}>X</button>

</div>

</main>

<style>
    div {
        position: relative;
        border: 1px solid black;
        border-radius: 8px;
        display: flex;
        overflow: hidden;
        margin: 8px 0;
    }

    .task-done {
        background-color: #1dd1a1;
        color: white;
    }

    input {
        margin: 0 16px;
    }

    button {
        position: absolute;
        right: 0;
        height: 100%;
        width: 64px;
        border: none;
        border-radius: 0;
        background-color: #ee5253;
        color: white;
        font-weight: 800;
        font-size: 22pt;
        font-family: 'Nunito';
        transition: .15s;
    }

    button:hover {
        background-color: #ffffff;
        color: #ee5253;
        transition: .15s;
    }
</style>