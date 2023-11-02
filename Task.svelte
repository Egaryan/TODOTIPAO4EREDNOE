<script>
  export let task;
  export let removeTask;
  export let toggleTask;
</script>

<li on:click={() => toggleTask(task.id)} class:completed={task.completed}>
  <input type="checkbox" bind:checked={task.completed}>
  {task.name}
  <button on:click={() => removeTask(task.id)}>Удалить</button>
</li>

<style>
  li {
    display: flex;
    align-items: center;
    margin: 5px 0;
    cursor: pointer;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
  }

  li.completed {
    text-decoration: line-through;
  }

  input[type="checkbox"] {
    margin-right: 10px;
  }

  button {
    margin-left: auto;
  }
</style>