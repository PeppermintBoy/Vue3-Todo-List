<template>
	<form @submit.prevent="submitInput">
		<label for="input">What do you have to do</label>
		<br />
		<input type="text" name="input" id="input" v-model="tempInput" />
		<br />
		<input type="submit" value="Submit" id="submit" />
	</form>
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
	methods: {
		submitInput() {
			this.submittedInput.name = this.tempInput;

			this.$emit('submittedInput', this.submittedInput);
		},
	},
	mounted() {
		document.getElementById('input').focus();
	},
};
</script>

<style scoped></style>
