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

<style lang="scss" scoped>
	@import "~styles/variables";
	@import "~styles/mixins";

	.pagination-wraper {
		display: flex;
		justify-content: center;
		font-size: 30px;
	}

	.pagination-btn {
		cursor: pointer;

		.fa-arrow-circle-left {
			@include arrow-circle(25px, white, 0.5);
		}

		.fa-arrow-circle-right {
			@include arrow-circle(25px, white, 0.5);
		}
	}

	.pages {
		color: $header-pagination;
		margin: 0px 8px;
	}
</style>
