<template>
	<li class='nav-link' v-if='model.code >= filterFrom && model.code <= filterTo'>
		<a href='#' class='nav-link' :class='{active: (model.code == 11)}' ><span class='code'>{{ model.code }}</span> {{ model.name }}</a>
		<ul class='nav flex-sm-column nav-pills' v-if='model.children'>
			<tree-item v-for='item in model.children' :model='item' :filterFrom='filterFrom' :filterTo='filterTo'></tree-item>
		</ul>
	</li>
</template>

<script>
	export default {
		name: 'tree-item',
		props: {
			model: Object,
			filterFrom: 0,
			filterTo: 0
		},
		data() { return {
			selected: false
		}}
	}
</script>

<style>
</style>