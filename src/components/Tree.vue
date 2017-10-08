<template>

<div>
  <div class='row'>
    <div class='col-md-6'>
      <h3>Tree view</h3>
    </div>
    <div class='col-md-6'>
      <h3>Filter</h3>
    </div>
  </div>

  <div class='row'>
  	<div class='col-md-6'>
  		<ul class='nav nav-pills nav-stacked col-md-12'>
  			<category-item v-for='category in categories' :key='category.code' :model='category'></category-item>
  		</ul>
  	</div>
  	<div class='col-md-6'>
  		Description of the selected product should appear here
  	</div>
  </div>
</div>

</template>

<script>
import CategoryItem from './CategoryItem'
import $ from 'jquery'

export default {
  name: 'tree',
  components: {
  	CategoryItem
  },
  data()  {

  return {
	    categories:
	  	[
	  		{
	  			name: 'One',
	  			code: 1,
	  			products: [
	  				{
			  			name: 'Apples',
			  			code: 1
			  		},	  				
			  		{
			  			name: 'Banana',
			  			code: 2
			  		},
			  		{
			  			name: 'Watermelon',
			  			code: 3
			  		}
	  			]
	  		},
	  		{
	  			name: 'Two',
	  			code: 2,
	  			products: [
	  				{
	  					name: 'Pineapple',
	  					code: 4
	  				},
	  				{
	  					name: 'Pumkin',
	  					code: 5
	  				}
	  			]
	  		},
	  		{
	  			name: 'Three',
	  			code: 3
	  		},
	  		{
	  			name: 'Four',
	  			code: 4
	  		},
	  		{
	  			name: 'Five',
	  			code: 5
	  		},
	  	]
	}
  }
}
</script>

<style>
	.item { padding: 5px 0; cursor: pointer;} 
	.code { color: #ccc; margin-right: 5px;}
	.child-container { margin-left: 20px;}
</style>