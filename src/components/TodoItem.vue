<template>
	<li>
		<span class="item-text" v-bind:class="{done: todo.completed}">
			<input type="checkbox" v-on:change="todo.completed = !todo.completed">
			<strong>{{index + 1}}</strong>
			<span>{{todo.title | uppercase}}</span>
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
		},
		filters: {
			uppercase(val) {
				return val.toUpperCase();
			}
		},
	}
</script>

<style scoped>
	li {
		border: 1px solid #eeeeee;
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: .5rem 1rem;
		margin: .5rem;
		text-align: left;
	}

	.item-text {
		padding-right: 20px;
		display: flex;
	}

	.item-text span {
		padding-left: 15px;
	}

	.btn-remove {
		background-color: red;
		border: none;
		color: #fff;
		border-radius: 50%;
		cursor: pointer;
		outline: none;
		flex-shrink: 0;
		width: 25px;
		height: 25px;
	}

	input {
		margin-right: 1rem;
	}

	.done {
		text-decoration: line-through;
	}
</style>