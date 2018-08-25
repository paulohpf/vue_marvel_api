<template>
	<div class="search">
		<input type="text" name="search" id="search" placeholder="Digite um HQ" v-model="search" @keypress.13="submit">
	</div>
</template>

<script>
	export default {
		name: 'Search',

		data() {
			return {
				search: ''
			}
		},

		methods: {
			submit() {
				this.$emit('submit', this.search);
			}
		}
	}
</script>

<style scoped>
.search {
	max-width: 700px;
	margin: 0 auto;
}

.search input {
	width: 100%;
	height: 36px;
	padding: 0 12px
}
</style>