<template>
  <div class="container">
    <CreateElements v-for="Recipe in DataList"  v-bind:key="Recipe.title"
      v-bind:title="Recipe.title"
      v-bind:thumbnail="Recipe.thumbnail"
      v-bind:href="Recipe.href"
      v-bind:ingredients="Recipe.ingredients"
    />
  </div>
</template>

<script>
import CreateElements from './CreateElements.vue' 
export default {
  name: 'FetchComponent',
  components: {
    CreateElements
  },
  data(){
    return{
      DataList: {},
      title: '',
      href: '',
      thumbnail: '',
      ingredients: '',
    }
  },  
  created(){
    const CORS = 'https://cors-anywhere.herokuapp.com/'
    const url = 'http://www.recipepuppy.com/api'

    fetch( CORS + url )
    .then( response => response.json() )
    .then( response => {
      this.DataList = response.results;
    })
    .catch(error =>{
      console.error(error)
    })
  }
}
</script>


<style scoped>
.container{
  display: grid;
  grid-template-columns: auto auto;
}
</style>
