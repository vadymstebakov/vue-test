<template>
	<li>
		<span v-bind:class="{done: todo.switched}">
			<input type="checkbox" v-on:change="todo.switched = !todo.switched">
			<strong>{{index + 1}}</strong>
			{{todo.title}}
		</span>
		<button class="btn-remove"
			@click="$emit('remove-todo', todo.id)"
		>&times;</button>
	</li>
</template>

<script>
	export default {
		props: {
			todo: {
				type: Object,
				required: true
			},
			index: Number
		}	
	}
</script>

<style scoped>
	li {
		border: 1px solid #eeeeee;
		display: flex;
		justify-content: space-between;
		padding: .5rem 1rem;
		margin: .5rem;
	}

	.btn-remove {
		background-color: red;
		border: none;
		color: #fff;
		border-radius: 50%;
		cursor: pointer;
		outline: none;
	}

	input {
		margin-right: 1rem;
	}

	.done {
		text-decoration: line-through;
	}
</style>