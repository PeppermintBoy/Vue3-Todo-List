<template>
	<div v-for="todo in todoList" :key="todo.name">
		<p v-if="!todo.done">Not done</p>
		<p v-else>Done</p>
		<p>{{ todo.name }}</p>
		<input type="checkbox" v-if="!todo.done" @click="todo.done = !todo.done" />
		<input type="checkbox" v-else @click="todo.done = !todo.done" checked />
	</div>
</template>

<script>
export default {
	props: ['todoList'],
};
</script>

<style scoped>
p {
	display: inline-block;
	margin: 10px;
}
</style>
