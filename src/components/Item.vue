<template>
	<div class="item-wraper">
		<label class="container">
			<input type="checkbox">{{ todo.text }}
			<span class="checkmark"></span>
		</label>
		<span class="remove-btn" @click="removeTodo"><i class="fa fa-minus-square-o" aria-hidden="true"></i></span>
	</div>
</template>

<script>
	export default {
		props: ['todo'],
		methods: {
			removeTodo() {
				this.$emit('removeItem', this.todo.id);
			}
		}
	}
</script>

<style scoped>
	.item-wraper {
		display: flex;
		justify-content: space-between;
		background: white;
		margin: 20px 10px 10px 10px;
		font-size: 21px;
		line-height: 55px;
		border-radius: 3px;
	}

	.container {
		display: block;
		position: relative;
		padding-left: 55px;
		cursor: pointer;
		-webkit-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
	}

	.container input {
		position: absolute;
		opacity: 0;
		cursor: pointer;
		height: 0;
		width: 0;
	}

	.checkmark {
		position: absolute;
		top: 0;
		left: 0;
		height: 25px;
		width: 25px;
		margin-top: 15px;
		margin-left: 15px;
		border-radius: 50%;
		border: 1px solid #008000a3;
	}

	/* On mouse-over, add a grey background color */
	.container:hover input ~ .checkmark {
		background-color: #ccc;
	}

	/* When the checkbox is checked, add a blue background */
	.container input:checked ~ .checkmark {
		background-color: #008004b5;

	}

	/* Create the checkmark/indicator (hidden when not checked) */
	.checkmark:after {
		content: "";
		position: absolute;
		display: none;
	}

	/* Show the checkmark when checked */
	.container input:checked ~ .checkmark:after {
		display: block;
	}

	/* Style the checkmark/indicator */
	.container .checkmark:after {
		left: 9px;
		top: 5px;
		width: 5px;
		height: 10px;
		border: solid white;
		border-width: 0 3px 3px 0;
		-webkit-transform: rotate(45deg);
		-ms-transform: rotate(45deg);
		transform: rotate(45deg);
	}

	.remove-btn {
		position: relative;
		top: 15px;
	}

	.remove-btn .fa-minus-square-o {
		font-size: 25px;
		padding: 5px;
		cursor: pointer;
		color: #8080809e;
	}

	.remove-btn .fa-minus-square-o:hover {
		color: red; 
	}
</style>
