<script>

    import TodoElement from "./TodoElement.svelte";

    var todos = [
        { text: "Test 1", isDone: false },
        { text: "Test 2", isDone: true }
    ]

    var newTask = ""

    function addTask() {
        if (newTask != "")
        {
            todos.push({ text: newTask, isDone: false })
            newTask = ""
            
            todos = todos
        }
    }

    function removeTask(taskIdx) {
        todos.splice(taskIdx, 1)

        todos = todos
    }

    function bite() {
        console.log("teub")
    }

</script>

<main>

    <h1>Tah la TODO List</h1>

    {#each todos as todo, idx}

        <TodoElement bind:text={todo.text} bind:done={todo.isDone} on:remove={() => removeTask(idx)}/>
        
    {/each}

    <div id="new-todo">
        <p>Ajouter une tâche</p>

        <input type="text" bind:value={newTask}>

        <button on:click={addTask}>OK</button>
    </div>

</main>

<style>

@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@200;400;600;800&display=swap');

main {
    font-family: 'Nunito';
    color: #222f3e;
}

#new-todo {
    position: absolute;
    bottom: 32px;
}

</style>