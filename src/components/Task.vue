<template>
	<li class="task">
		<div class="task--checker">
			<input type="checkbox" class="task--check" @change="checkToogle" v-model="task.completed" :id="task.id">
			<label class="task--name" :for="task.id">
				{{ task.task }}
			</label>
		</div>
		<div class="task--delete">
			<a href="#" class="task--delete--link" :data-id="task.id" @click="$emit('delete-task', task.id)">Delete</a>
		</div>
	</li>
</template>
<script>
export default {
	name: 'Task',
	props: {
		task: Object
	},
	methods: {
		checkToogle(e) {
			console.log(`[Checked] Task ${e.target.id}`);
		}
	}
}
</script>
<style type="text/css" scoped>

	.task {
		margin: .3rem;
		display: flex;
		align-items: center;
		justify-content: space-between;
	}

	.task--checker {
		display: flex;
		align-items: center;
	}

	.task--check {
		background-color: red;
	}

	.task--check:checked + .task--name {
		text-decoration: line-through;
		color: #797979;
	}

	.task--name {
		margin-left: .5rem;
		font-weight: 500;
	}

	.task--delete--link {
		font-size: .9rem;
		color: red;
		text-decoration: none;
	}

	.task--delete--link:hover {
		color: #FD6246;
	}

</style>
