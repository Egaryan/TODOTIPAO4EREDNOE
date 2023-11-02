<script>
  import Task from "./Task.svelte";
  import { count } from "./Store.js";
  export let tasks;
  export let filter;
  export let removeTask;
  export let toggleTask;

  function countTasks(filter) {
    if (filter === "completed") {
      return tasks.filter(task => task.completed).length;
    } else if (filter === "active") {
      return tasks.filter(task => !task.completed).length;
    } else {
      return tasks.length;
    }
  }

  let count_value;

  count.subscribe(value => {
    count_value = value;
  });
</script>

<button on:click={() => {$count = + 1} }>Добавить</button>

<h1>{$count}</h1>

<style>
  ul {
    list-style: none;
    padding: 0;
  }

  div {
    text-align: center;
    margin-top: 10px;
  }

  button {
    margin: 0 5px;
  }
</style>

<menu/>