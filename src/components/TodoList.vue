<template>
	<div>
		<p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
		<p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
		<todo v-for="todo in todos" v-bind:todo="todo" v-bind:key="todo.id" v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo"></todo>
	</div>
</template>

<script type="text/javascript">

import sweetalert from 'sweetalert';
import Todo from "./Todo.vue";

export default {
	props: ['todos'],
	components: {
		Todo,
	},
	methods: {
		deleteTodo(todo){
			const todoIndex = this.todos.indexOf(todo);
			this.todos.splice(todoIndex, 1);
			sweetalert('Deleted!', 'Your Task has been deleted.', 'success');
		},
		completeTodo(todo){
			const todoIndex = this.todos.indexOf(todo);
			this.todos[todoIndex].done = true;
			sweetalert('Success!', 'Task completed!', 'success');
		},
	},
};
</script>

<style></style>


