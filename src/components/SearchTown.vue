<template>
	<div class="container">
		<form @submit.prevent="onSubmit">
			<input
				type="search" placeholder="Укажите город.."
				v-model="searchText"
			>
			<button type="submit">Найти</button>
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
			console.log(this.searchText);
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
