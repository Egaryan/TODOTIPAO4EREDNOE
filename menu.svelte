<scrtipt>

	import { count } from '/Store.js';

</scrtipt>

<ul>
	{#if tasks.length > 0}
	<div>
		<button on:click={()=> filter = 'all'}>Все</button>
		<button on:click={()=> filter = 'completed'}>Выполненные</button>
		<button on:click={()=> filter = 'active'}>Незавершенные</button>
	</div>
	{/if}
	{#each tasks as task (task.id)}
	{#if filter === 'all' || (filter === 'completed' && task.completed) || (filter === 'active' && !task.completed)}
	<Task {task} {removeTask} {toggleTask} />
	{/if}
	{/each}
</ul>