<template>
  <div id="Components">
    <div v-if="this.Loading">
      <div id="spinner"></div>
      <h2> Loading </h2>
    </div>
    <div class="container">
      <CreateElements v-for="Recipe in DataList"  v-bind:key="Recipe.title"
        v-bind:title="Recipe.title"
        v-bind:thumbnail="Recipe.thumbnail"
        v-bind:href="Recipe.href"
        v-bind:ingredients="Recipe.ingredients"
      />
    </div>
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
      Loading: true,
      searchQuery: ''
    }
  },  
  created(){
    const CORS = 'https://cors-anywhere.herokuapp.com/'
    const url = 'http://www.recipepuppy.com/api'

    fetch( CORS + url )
    .then( response => response.json() )
    .then( response => {
      this.Loading = false;
      this.DataList = response.results;
    })
    .catch(err =>{
      console.log('Error', err)
    })
  }
}
</script>


<style scoped>
#Components{
  text-align: center;
}
.container{
  display: grid;
  grid-template-columns: auto auto;
}
.form-control{
  margin: 26px;
  width: 350px;
  padding: 5px;
}
#spinner {
  width: 60px;
  height: 60px;
  margin: 100px auto 35px;
  border: 15px solid #f3f3f3;
  border-top: 15px solid #29be3d; 
  border-radius: 50px;
  animation: spin 1s linear infinite;
}
h2{
  color: white;
}
@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}
</style>
