<template>
	<div class="form-group">
		<input type="text" v-model="inputText" @keyup.enter="addTodo" placeholder="What do you need to do?">
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
			addTodo() {
				this.$emit('addItem', this.inputText);
				this.inputText = '';
			}
		}
	}
</script>

<style scoped>
	.form-group {
		display: flex;
		margin: 0px 10px;
	}

	input {
		width: 100%;
		border: none;
		border-bottom: 2px solid #f0e9e9e3;
		line-height: 38px;
		font-size: 23px;
		margin-right: 10px;
		background-color: transparent;
		color: white;
	}

	input:focus {
		outline: none;
		border: none;
		border-bottom: 2px solid #f0e9e9e3;
	}

	input::-webkit-input-placeholder {
		color: #f0e9e9e3 !important;
		opacity: 0.4;
	}
	 
	input:-moz-placeholder { 
		color: #f0e9e9e3 !important;
		opacity: 0.4;  
	}
	 
	input::-moz-placeholder {  
		color: #f0e9e9e3 !important;
		opacity: 0.4;  
	}
	 
	input:-ms-input-placeholder {  
		color: #f0e9e9e3 !important;
		opacity: 0.4;  
	}

	.submit-button {
		border: 1px solid white;
		padding: 8px;
		border-radius: 4px;
		cursor: pointer;
		color: white;	
	}

	.submit-button:hover {
		box-shadow: 0px 0px 15px #0000009c; 
	}
</style>
