<template>
	<li>
		<div class='btn-group'>
			<div class='btn btn-success'>Category {{ model.name }}</div> 
			<span class='btn btn-default' v-if='productCount != 0'>{{ productCount }} items</span>
			<div class='btn btn-default' @click='expanded = !expanded'>
				<span v-if='expanded'>Collapse &uarr;</span>
				<span v-if='!expanded'>Expand &darr;</span>
			</div>
		</div>
		<div class='list-group-item' v-show='expanded'>

		<div class='form-inline row'>
	  		<div class='form-group col-md-3'>
	  			<label for='filterFrom'>Code From</label>
	  			<input class='form-control' type='number' v-model='filterFrom'/>
	  		</div>
	  		<div class='form-group col-md-3'>
	  			<label for='filterTo'>Code To</label>
	  			<input class='form-control' type='number' v-model='filterTo'/>
	  		</div>	  		
	  		<div class='form-group col-md-3'>
	  			<label for='filterDescription'>Name</label>
	  			<input class='form-control' type='text' v-model='filterName'/>
	  		</div>
	  	</div>

		<ul class='nav nav-stacked margin-top-15' v-if='productCount > 0'>
			<product-item v-for='product in model.products' :key='product.code' :model='product' :filterFrom='filterFrom' :filterTo='filterTo' :filterName='filterName'></product-item>
		</ul>
		<div class='text-muted' v-if='productCount == 0'>
			No products
		</div>
		</div>
	</li>
</template>

<script>

	import ProductItem from './ProductItem'

	export default {
		name: 'category-item',
		components: {
			ProductItem
		},
		created: function(){
			this.filterFrom = this.minCode;
			this.filterTo = this.maxCode;
		},
		props: {
			model: Object
		},		
		computed: {
			productCount: function(){
				var self = this;

				return self.model.products == null 
					? 0 
					: self.model.products.filter((item) => { return item.code >= self.filterFrom && item.code <= self.filterTo 
						&& item.name.toLowerCase().indexOf(this.filterName.toLowerCase()) >= 0}).length;
			},
			minCode: function(){
				var self = this;

				return self.model.products == null 
					? 0 
					: self.model.products.sort((a,b) => { return a.code - b.code})[0].code;				

			},
			maxCode: function(){
				var self = this;

				return self.model.products == null 
					? 0 
					: self.model.products.sort((a,b) => { return a.code - b.code})[self.model.products.length - 1].code;				
			},

		},
		data(){
			return {
				expanded: true,
				filterFrom: 0,
				filterTo: 0,
				filterName: ''
			}
		}
	}

</script>