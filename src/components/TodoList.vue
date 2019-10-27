<template>
	<div>
		<ul>
			<TodoItem 
				v-for="(todo, i) of todoArr"
				:key="todo.title"
				:todo="todo"
				:index="i"
				@remove-todo="removeTodo"
			/>
		</ul>
	</div>
</template>

<script>
	import TodoItem from '@/components/TodoItem';
	export default {
		props: ['todoArr'],
		components: {
			TodoItem
		},
		methods: {
			removeTodo(id) {
				this.$emit('remove-todo', id);
			}
		},
	}
</script>

<style scoped>
	ul {
		list-style: none;
		margin: 0;
		padding: 0;
	}
</style>