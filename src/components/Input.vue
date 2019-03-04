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

<style lang="scss" scoped>
	@import "~styles/variables";

	.form-group {
		display: flex;
		margin: 0px 10px;
	}

	input {
		width: 420px;
		border: none;
		border-bottom: $input-border-bottom;
		line-height: 38px;
		font-size: 23px;
		background-color: transparent;
		color: white;
	
		&:focus {
			outline: none;
			border: none;
			border-bottom: $input-border-bottom;
		}

		&::-webkit-input-placeholder {
			color: $input-placeholder-color;
			opacity: $input-placeholder-opacity;
		}
		 
		&:-moz-placeholder { 
			color: $input-placeholder-color;
			opacity: $input-placeholder-opacity;  
		}
		 
		&::-moz-placeholder {  
			color: $input-placeholder-color;
			opacity: $input-placeholder-opacity;  
		}
		 
		&:-ms-input-placeholder {  
			color: $input-placeholder-color;
			opacity: $input-placeholder-opacity;  
		}
	}
</style>
