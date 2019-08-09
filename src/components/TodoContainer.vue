<template>
	<div class="todo-container">
		<h2 class="category-title">Main</h2>
		<CreateTask />
		<div class="tasks">
			<div v-if="totalTasks">
				<ul class="tasks-list">
					<Task v-for="task in tasks" :task="task" :key="task.id" @delete-task="$emit('delete-task', task.id)"/>
				</ul>
				<p class="tasks-completed">
					<span v-if="everythingDone" class="everything-done">Everything done!</span>
					<span v-else>{{ completedTasks }}/{{ totalTasks }} tasks completed</span>
				</p>
			</div>
			<div v-else >
				<p class="no-tasks">No tasks!</p>
			</div>
		</div>
	</div>
</template>

<script>
import Task from './Task.vue'
import CreateTask from './CreateTask.vue'

export default {
	name: 'TodoContainer',
	props: {
		tasks: Array
	},
	components: {
		Task,
		CreateTask
	},
	computed: {
		totalTasks() {
			return this.tasks.length;
		},
		completedTasks() {
			return this.tasks.filter(task => task.completed).length;
		},
		everythingDone() {
			var completed = this.completedTasks === this.totalTasks;

			if (completed) {
				console.log('Everything done!');
			}

			return completed
		},
	}
}
</script>

<style type="text/css" scoped>

	.todo-container {
		max-width: 700px;
		margin: 0 auto;
	}

	.category-title {
		color: #0f0f0f;
		text-align: left;
		padding-bottom: .7rem;
	}

	@media (max-width: 768px) {
		.category-title {
			text-align: center;
		}
	}

	.tasks-list {
		list-style: none;
	    border: 1px solid #a0a0a0;
	    padding: 1em;
	}

	.tasks-completed {
		border: 1px solid #a0a0a0;
		color: #545454;
		font-weight: 500;
		font-size: .9em;
		text-align: center;
		margin-top: 1.5rem;
		padding: .5rem;
	}

	.everything-done {
		color: #0f0f0f;
		font-weight: bold;
		text-align: center;
		margin-top: 1em;
	}

	.no-tasks {
		color: #545454;
		margin-top: .5em;
	    border: 1px solid #a0a0a0;
	    padding: 5px;
	    font-size: .9em;
	    text-align: center;
	}

</style>
