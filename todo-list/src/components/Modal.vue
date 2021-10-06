<template>
	<div class="backdrop" @click.self="closeModal">
		<form class="modal" @submit.prevent="submitInput">
			<input type="text" name="input" id="input" v-model="tempInput" />
			<br />
			<input type="submit" value="Add task" id="submit" />
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			tempInput: '',
			submittedInput: {
				done: false,
				name: '',
			},
		};
	},
	emits: ['submittedInput', 'closeModal'],
	methods: {
		submitInput() {
			this.submittedInput.name = this.tempInput;

			this.$emit('submittedInput', this.submittedInput);
		},
		closeModal() {
			this.$emit('closeModal');
		},
	},
	mounted() {
		document.getElementById('input').focus();
	},
};
</script>

<style scoped>
.backdrop {
	top: 0;
	position: fixed;
	background: rgba(0, 0, 0, 0.5);
	width: 100%;
	height: 100%;
}

.modal {
	width: 400px;
	padding: 20px;
	margin: 100px auto;
	background: white;
	border-radius: 10px;
}
#input {
	border-radius: 10px;
	width: 60%;
}
</style>
