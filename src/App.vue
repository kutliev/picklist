<template>
  <div id='app'>
    <div class='container'>
      <div class='header'>
        <h1 class='text-muted'>Picklist</h1>
        <hr/>
      </div>
      <tree></tree>
    </div>
  </div>
</template>

<script>
import Tree from './components/Tree'

export default {
  name: 'app',
  components: {
    Tree
  }
}
</script>

<style>
  #app {  }
  .margin-top-15 { margin-top: 15px; }
</style>
