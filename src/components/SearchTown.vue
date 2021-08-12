<template>
	<div class="container">
		<form @submit.prevent="onSubmit">
			<input
				class="form-control"
				type="search" placeholder="Укажите город.."
				v-model="searchText"
			>
			<button class="btn btn-dark" type="submit">Найти</button>
		</form>
	</div>
</template>

<script>
export default {
	data() {
		return {
			searchText: ''
		}
	},
	methods: {
		onSubmit() {
			if(this.searchText.trim()) {
				this.$emit('search', this.searchText);
				this.searchText = '';
			}
		}
	}
}
</script>

<style scoped>
	form {
		display: flex;
		max-width: 700px;
		margin: 0 auto;
		margin-bottom: 20px;
	}

	input {
		width: 100%;
		margin-right: 10px;
		padding: 10px;
	}
</style>
