<script>
	import TodoList from './components/TodoList.svelte'
</script>
  
<main>
	<div class="header">
		<span>
			Abigail Thelin - Svelte Todo App
		</span>
	</div>
	<TodoList />
</main>

<style>
	.header {
		padding: 4px 16px;
		background-color: #9c27b0;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		height: 64px;
		font-size: 1.25rem;
		font-family: 'Roboto', sans-serif;
		box-shadow: 0px 2px 8px #888888;
	}
	.header span {
		color: white;
	}
</style> 