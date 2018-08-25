<template>
	<div class="list">
		<Item v-for="item in items" :key="item.id" :item="item"></Item>
	</div>
</template>

<script>
	import Item from './Item';

	export default {
		name: 'List',
		props: {
			items: {
				required: true,
				type: Array
			}
		},

		components: {
			Item
		}
	}
</script>

<style scoped>
.list {
	max-width: 960px;
	text-align: left;
	margin: 0 auto;
}
</style>