<template>
	<img alt="Vue logo" src="./assets/logo.png" />
	<button @click="toggleModal">Add new task</button>
	<teleport to=".modals" v-if="modalShown">
		<Modal @submittedInput="submittedInput = $event" />
	</teleport>
	<div>
		<h1>Yoyo's Todo List</h1>
		<p>{{ submittedInput }}</p>

		<Forms />
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
		};
	},
	methods: {
		toggleModal() {
			this.modalShown = !this.modalShown;
		},
	},
};
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
