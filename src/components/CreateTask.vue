<template>
	<form class="task-create" @submit="createTask">
		<input type="text" name="taskInput" class="task-create--input" v-model="task" placeholder="New task...">
		<button type="submit" class="task-create-button">Add Task</button>
	</form>
</template>


<script>
	export default {
		name: 'CreateTask',
		data() {
			return {
				task: ''	
			}
		},
		methods: {
			createTask(e) {
				e.preventDefault();
				console.log('[Created] Task __new__');
				this.task = '';
			}
		}
	}
</script>
	

<style scoped>

.task-create {
	padding: 1em 0;
	display: grid;
	grid-template-columns: 1fr auto;
	grid-column-gap: 1em;
}

.task-create--label {
	font-weight: 500;
	margin-right: .5rem;
}

.task-create--input {
	padding: 7px;
	font-size: .9em;
	border: 1px solid #a0a0a0;
}

.task-create--input:focus {
	outline: 0 !important;
}

.task-create-button {
    background-color: #fff;
    border: 1px solid #a0a0a0;
    padding: 4px 8px;
}

.task-create-button:hover {
	cursor: pointer;
    background-color: #eee;
}

.task-create-button:focus, .task-create-button:active {
	outline: 0 !important;
}

</style>
