<template>
	<div class="header">
		<h1>VueJS Todo List</h1>
	</div>
</template>

<script>
export default {
	name: 'Header'
}	
</script>


<style type="text/css" scoped>

	.header {
		margin: 4rem 0;
		text-align: center;
	}

	@media (max-width: 768px) {
		.header {
			margin: 3rem 0;
		}
	}

</style>
