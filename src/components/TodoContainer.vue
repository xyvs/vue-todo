<template>
	<div class="todo-container">
		<h2 class="category-title">Main</h2>
		<ul class="tasks-list">
			<Task v-for="task in tasks" :task="task" :key="task.id" />
		</ul>
		<p class="tasks-completed">
			<span v-if="everythingDone" class="everything-done">You're awesome!</span>
			<span v-else>{{ completedTasks }}/{{ totalTasks }} tasks completed</span>
		</p>
	</div>
</template>

<script>
import Task from './Task.vue'

export default {
	name: 'TodoContainer',
	props: {
		tasks: Array
	},
	components: {
		Task
	},
	computed: {
		totalTasks() {
			return this.tasks.length
		},
		completedTasks() {
			return this.tasks.filter(task => task.completed).length
		},
		everythingDone() {
				return this.completedTasks === this.totalTasks
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
	}

	.tasks-completed {
		border: 1px solid #a0a0a0;
		color: #a0a0a0;
		font-weight: 500;
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

</style>
