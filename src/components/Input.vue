<template>
	<div class="input-field">
		<input type="text" v-model="inputText">
		<button class="submit-button" @click="addText">Submit</button>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				inputText: ""
			}
		},
		methods: {
			addText() {
				this.$emit('todo:add', this.inputText);
				this.inputText = '';
			}
		}
	}
</script>

<style scoped>
	input {
		width: 75%;
		border: none;
		border: 2px solid blue;
		margin-right: 10px;
		padding: 5px;
		line-height: 17px;
	}

	input:focus {
		outline: none;
		border: none;
		border: 2px solid blue;
		border-bottom: 2px solid blue;
	}

	.submit-button {
		background: #2196F3;
		border: 2px solid blue;
		padding: 5px;
		border-radius: 4px;
		cursor: pointer;	
	}

	.submit-button:hover {
		box-shadow: 0px 0px 15px #0000009c; 
	}
</style>