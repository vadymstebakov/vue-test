<template>
  	<div>
		<h2>TODO application</h2>
		<router-link to="/">Home</router-link>
		<AddTodo 
			@add-todo="addTodo"
		/>
		<select v-model="filter">
			<option value="all">All</option>
			<option value="completed">Completed</option>
			<option value="not-completed">Not-completed</option>
		</select>
		<hr>
		<Loader v-if="loading"/>
		<TodoList
			v-else-if="filteredTodo.length"
			:todoArr = "filteredTodo"
			@remove-todo = "removeTodo"
		/>
		<p v-else>No todos!</p>
	</div>
</template>

<script>
	import TodoList from '@/components/TodoList';
	import AddTodo from '@/components/AddTodo';
	import Loader from '@/components/Loader';

	export default {
		name: 'app',
		data() {
			return {
				todoArr: [
					// {id: 1, title: 'first', completed: false},
					// {id: 2, title: 'second', completed: false},
					// {id: 3, title: 'third', completed: false},
				],
				loading: true,
				filter: 'all',
			}
		},
		mounted() {
			fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
				.then(response => response.json())
				.then(json => {
					setTimeout(() => {
						this.todoArr = json;
						this.loading = false;
					}, 1000);
				});
		},
		// watch: {
		// 	filter(val) {
		// 		console.log(val);
				
		// 	}
		// },
		computed: {
			filteredTodo() {
				if (this.filter === 'all') return this.todoArr;

				if (this.filter === 'completed') {
					return this.todoArr.filter(t => t.completed);
				}

				if (this.filter === 'not-completed') return this.todoArr.filter(t => !t.completed);
			}
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
			AddTodo,
			Loader,
		}
	};
</script>