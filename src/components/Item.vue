<template>
	<div class="item-wraper">
		<label class="container">
			<input type="checkbox" id="todo" value="todo" v-model="todo.checked">
			<label class="strikethrough">{{ todo.text }}</label>
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

<style lang="scss" scoped>
	@import "~styles/mixins";

	.item-wraper {
		background: white;
		margin: 20px 10px 10px 10px;
		font-size: 21px;
		border-radius: 3px;
		width: 420px;
		word-wrap: break-word;
	}

	.container {
		display: block;
		position: relative;
		padding-left: 25px;
		cursor: pointer;
		@include item-container-vendors;

		input {
			opacity: 0;
			cursor: pointer;
		}

		&:hover input ~ .checkmark {
			background-color: #ccc;
		}

		input:checked ~ .checkmark {
			background-color: #008004b5;

			&:after {
				display: block;
			}
		}

		.checkmark:after {
			left: 9px;
			top: 5px;
			width: 5px;
			height: 10px;
			border: solid white;
			border-width: 0 3px 3px 0;
			@include transform(rotate(45deg));
		}
	}

	.checkmark {
		position: absolute;
		top: 15px;
		left: 15px;
		height: 25px;
		width: 25px;
		border-radius: 50%;
		border: 1px solid #008000a3;

		&:after {
			content: "";
			position: absolute;
			display: none;
		}
	}

	.strikethrough {
		position: relative;
		top: 17px;
		left: 4px;
	}

	input[type=checkbox]:checked + label.strikethrough {
		text-decoration: line-through;
	}

	.remove-btn {
		position: relative;
		top: 4px;
		left: 388px;

		.fa-minus-square-o {
			font-size: 25px;
			padding: 5px;
			cursor: pointer;
			color: #8080809e;

			&:hover {
				color: red; 
			}
		}
	}
</style>
