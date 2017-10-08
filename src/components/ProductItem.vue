<template>
	<li v-if='model.code >= filterFrom && model.code <= filterTo  && model.name.toLowerCase().indexOf(filterName.toLowerCase()) >= 0'>
		<a href='#' class='nav-link' :class='{active: (model.code == 2)}' ><span class='code'>{{ model.code }}</span> {{ model.name }}</a>
	</li>
</template>

<script>
	export default {
		name: 'product-item',
		props: {
			model: Object,
			filterFrom: 0,
			filterTo: 0,
			filterName: ''
		},
		data() { return {
			selected: false
		}}
	}
</script>
