<template>
	<div class="item-wraper">
		<button class="remove-btn" @click="removeTodo">Remove</button>{{ todo.text }}
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
		border-bottom: 1px solid gray;
		text-align: left;
		margin: 20px 10px 10px 10px;
		font-size: 18px;
	}

	.remove-btn {
		background: #ff00009e;
		border: 2px #ff00009e;
		padding: 5px;
		border-radius: 4px;
		cursor: pointer;
		margin-right: 20px;
		margin-bottom: 10px;
	}

	.remove-btn:hover {
		box-shadow: 0px 0px 15px #0000009c;
	}
</style>