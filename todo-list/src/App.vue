<template>
	<img id="yoyo-logo" alt="yoyo's logo" src="./assets/Nathan.jpeg" />
	<br />
	<h1>Yoyo's Todo List</h1>
	<button @click="toggleModal">Add new task</button>
	<div to=".modals" v-if="modalShown">
		<Modal
			@submittedInput="
				(submittedInput = $event), toggleModal(), pushToTodoList()
			"
			@closeModal="toggleModal()"
		/>
	</div>
	<div>
		<Forms :todo-list="todoList" @delete-task="deleteTask($event)" />
	</div>
</template>

<script>
import Forms from './components/Forms.vue';
import Modal from './components/Modal.vue';
export default {
	name: 'App',
	components: {
		Forms,
		Modal,
	},
	data() {
		return {
			modalShown: false,
			submittedInput: '',
			todoList: [],
		};
	},
	methods: {
		toggleModal() {
			this.modalShown = !this.modalShown;
		},
		pushToTodoList() {
			this.todoList.push(this.submittedInput);
		},
		deleteTask(i) {
			this.todoList.splice(i, 1);
		},
	},
};
</script>

<style>
body {
	text-align: center;
}
#yoyo-logo {
	margin: 0 auto;
	width: 100px;
	height: 100px;
	text-align: center;
	border-radius: 50%;
}
</style>
