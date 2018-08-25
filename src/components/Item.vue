<template>
	<div class="item">
		<div class="item__image">
			<img alt="Comics" v-bind:src="image" />
		</div>
		<div class="item__content">
			<div class="item__title">
				{{ item.title }}
			</div>
			<div class="item__modified">
				{{ item.modified }}
			</div>
			<div class="item__description">
				{{ item.description }}
			</div>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'Item',

		props: {
			item: {
				required: true,
				type: Object
			}
		},

		computed: {
			image() {
				return this.item.images[0].path + '.' + this.item.images[0].extension;
			}
		}
	}
</script>

<style scoped>
.item {
	width: 320px;
	display: inline-block;
	padding: 10px;
	vertical-align: top;
}
.item__image img {
	width: 300px;
	height: 450px;
}
.item__content {
	text-align: left;
}
.item__title {
	font-weight: bold;
	text-transform: uppercase;
}
.item__modified {
	font-size: 12px;
}
.item__description {
	text-align: justify;
	width: 270px;
	white-space: nowrap;
	overflow: hidden;
	text-overflow: ellipsis;
	height: 20px;
}
</style>