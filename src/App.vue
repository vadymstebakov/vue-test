<template>
  	<div id="app">
		<h1>TODO application</h1>
		<AddTodo 
			@add-todo="addTodo"
		/>
		<TodoList 
			v-bind:todoArr = "todoArr"
			@remove-todo = "removeTodo"
		/>
	</div>
</template>

<script>
	import TodoList from '@/components/TodoList';
	import AddTodo from '@/components/AddTodo';

	export default {
		name: 'app',
		data() {
			return {
				todoArr: [
					{id: 1, title: 'first', switched: false},
					{id: 2, title: 'second', switched: false},
					{id: 3, title: 'third', switched: false},
				]
			}
		},
		mounted() {
			fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
				.then(response => response.json())
				.then(json => {
					this.todoArr = json
				})
		},
		methods: {
			removeTodo(id) {
				this.todoArr = this.todoArr.filter(t => t.id !== id);
			},
			addTodo(todo) {
				this.todoArr.push(todo);
			}
		},
		components: {
			TodoList,
			AddTodo
		}
	};
</script>

<style>
	#app {
		font-family: "Avenir", Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
