<template>
	<div id="app">
		<Header/>
		<TodoContainer :tasks="tasks" @delete-task="deleteTask"/>
	</div>
</template>

<script>
import Header from './components/layout/Header.vue'
import TodoContainer from './components/TodoContainer.vue'

export default {
	name: 'app',
	components: {
		Header,
		TodoContainer
	},
	data() {
		return {
			tasks: [
				{
					id: 1,
					task: 'Example task',
					completed: false
				},
				{
					id: 2, 
					task: 'Learn AWS',
					completed: false
				},
				{
					id: 3,
					task: 'Another task test',
					completed: true
				},
				{ 
					id: 4, 
					task: 'Make a projects reviews',
					completed: false
				},
				{ 
					id: 5, 
					task: 'ReactJS todo list',
					completed: false
				}
			]
		}
	},
	methods: {
		deleteTask(id) {
			console.log(`[Deleted] Task ${id}`);
			this.tasks = this.tasks.filter(task => task.id !== id);
		}
	},
}
</script>

<style>

	* {
		padding: 0;
		margin: 0;
	}

	@media (max-width: 768px) {
		body {
			padding: 1.5em;
		}
	}

	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}

</style>
