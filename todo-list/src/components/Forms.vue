<template>
	<button
		v-show="todoList.length"
		class="all-done"
		@click="toggleAllDone(todoList)"
	>
		All done
	</button>
	<div class="todo" v-for="todo in todoList" :key="todo.name">
		<input
			type="checkbox"
			@click="todo.done = !todo.done"
			:checked="todo.done"
		/>
		<p :class="{ done: todo.done }">{{ todo.name }}</p>
		<button @click="deleteTask(todo, todoList)">X</button>
	</div>
</template>

<script>
export default {
	props: ['todoList'],
	data() {
		return {};
	},
	emits: ['deleteTask'],
	methods: {
		deleteTask(todo, todoList) {
			// when you pass in an object as props, use ... to show the data
			// console.log(...this.todoList);

			//My way
			// for (let i = 0; i < todoList.length; i++) {
			// 	if (todoList[i].name == todo.name) {
			// 		return this.$emit('deleteTask', i);
			// 	}
			// }

			//Youtuber's way
			const todoIndex = todoList.indexOf(todo);
			return this.$emit('deleteTask', todoIndex);
		},
		toggleAllDone(todoList) {
			//My way
			// for (let i = 0; i < todoList.length; i++) {
			// 	todoList[i].done = true;
			// }

			//youtuber's way
			todoList.forEach(todo => (todo.done = true));
		},
	},
};
</script>

<style scoped>
p {
	display: inline-block;
	margin: 10px;
}
.done {
	text-decoration: line-through;
}

.todo {
	font-size: 20px;
}

.todo button {
	color: white;
	background-color: red;
	border-style: none;
	cursor: pointer;
	border-radius: 10px;
}

.todo button:hover {
	background-color: rgba(78, 3, 163, 0.466);
}

.all-done {
	background-color: rgb(28, 185, 7);
	color: rgb(244, 248, 0);
	border-radius: 10px;
	border-style: none;
	margin-top: 30px;
	font-size: 20px;
	font-family: 'Indie Flower', cursive;
}
</style>
