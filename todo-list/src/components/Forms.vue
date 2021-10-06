<template>
	<div v-for="todo in todoList" :key="todo.name">
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

			for (let i = 0; i < todoList.length; i++) {
				if (todoList[i].name == todo.name) {
					return this.$emit('deleteTask', i);
				}
			}
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

button {
	color: white;
	background-color: red;
	border-style: none;
	cursor: pointer;
	border-radius: 10px;
}

button:hover {
	background-color: rgba(78, 3, 163, 0.466);
}
</style>
