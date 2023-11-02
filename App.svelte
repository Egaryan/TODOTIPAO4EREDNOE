<script>
  import TaskList from "./TaskList.svelte";
  let newTask = "";
  let tasks = [];
  let filter = "all"; // Добавляем эту строку для определения filter

  function addTask() {
    if (newTask.trim() !== "") {
      tasks = [...tasks, { id: Date.now(), name: newTask, completed: false }];
      newTask = "";
    }
  }

  function removeTask(id) {
    tasks = tasks.filter(task => task.id !== id);
  }

  function toggleTask(id) {
    tasks = tasks.map(task => {
      if (task.id === id) {
        return { ...task, completed: !task.completed };
      }
      return task;
    });
  }

  function countTasks(filter) {
    if (filter === "completed") {
      return tasks.filter(task => task.completed).length;
    } else if (filter === "active") {
      return tasks.filter(task => !task.completed).length;
    } else {
      return tasks.length;
    }
  }
</script>

<main>
  <h1>Список дел</h1>

  <input type="text" bind:value={newTask} placeholder="Новая задача">
  <button on:click={addTask}>Добавить</button>

  <TaskList {tasks} {filter} {removeTask} {toggleTask} />

  <div>
    <span>Задачи: {countTasks('all')}</span>
    <span>Завершенные: {countTasks('completed')}</span>
    <span>Незавершенные: {countTasks('active')}</span>
  </div>
</main>

<style>
  main {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    font-family: Arial, sans-serif;
  }

  h1 {
    text-align: center;
  }

  input,
  button {
    margin-top: 10px;
    width: 100%;
  }
</style>