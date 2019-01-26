<template>
	<div v-if="totalPage() > 0" class="pagination-wraper">
		<span v-if="previousLink()" class="pagination-btn" @click="updatePage(currentPage - 1)"><i class="fa fa-arrow-circle-left" aria-hidden="true"></i></span>
		<span class="pages">{{ currentPage + 1 }} of {{ totalPage() }}</span>
		<span v-if="nextLink()" class="pagination-btn" @click="updatePage(currentPage + 1)"><i class="fa fa-arrow-circle-right" aria-hidden="true"></i></span>
	</div>
</template>

<script>
	export default {
		props: ['todos', 'currentPage', 'pageSize'],
		methods: {
			updatePage(pageNumber) {
				this.$emit('updatePage', pageNumber);
			},
			totalPage() {
				return Math.ceil(this.todos.length / this.pageSize);
			},
			previousLink() {
				if (this.currentPage != 0) {
					return true;
				}
			},
			nextLink() {
				if (this.currentPage != (this.totalPage() - 1)) {
					return true;
				}
			}
		}
	}
</script>

<style>
	.pagination-wraper {
		padding: 8px;
		margin: 20px 150px;
		font-size: 30px;
	}

	.pagination-btn {
		cursor: pointer;
	}

	.pagination-btn .fa-arrow-circle-left {
		font-size: 25px;
		color: white;
	}

	.pagination-btn .fa-arrow-circle-right {
		font-size: 25px;
		color: white;
	}

	.pages {
		color: black;
	}
</style>
