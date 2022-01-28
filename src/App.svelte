<script>
	let toDoList=[
		{
			title:"Learn Svelte",
			completed:false
		},
		{
			title:"Learn Sapper",
			completed:false
		},
		{
			title:"Learn SvelteKit",
			completed:false
		}
	]

	let newItem='';
	
	function addToDo(toDo){
		toDoList.push({title: toDo, completed: false})
		toDoList = toDoList;
	}

	function removeTodo(index){
		toDoList.splice(index, 1);
		toDoList = toDoList;
	}
</script>
<div class="center">
	<header>
		Svelte To Do App
	</header>

	<br />

	<input bind:value={newItem} type="text" placeholder="Insert new to do item">
	<button on:click={addToDo(newItem)}>Add</button>

	<br />

	{#each toDoList as item, index}
		<input type="checkbox" bind:checked={item.completed}>
		<span class:checked={item.completed}>{item.title}</span>
		<button on:click={() => removeTodo(index)}>❌</button>
		<br />
	{/each}
</div>

<style>
	header {
		font-size: 2em;
	}

	.center {
		text-align: center;
	}

	.checked {
		text-decoration: line-through;
	}
</style>
