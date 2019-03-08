<template>
  <div id="app">
    <div id="Logo" >
      <img alt="Vue logo" src="./assets/logo.png">
    </div>
    <FetchComponent/>
  </div>
</template>

<script>
import FetchComponent from './components/FetchComponent.vue'

export default {
  name: 'app',
  components: {
    FetchComponent
  }
}
</script>

<style>
  body{
    margin: 0; padding: 0;
  }
  #Logo{
    background-color: white;
    width: 100%;
    margin: 0;
    padding: 0;
  }
  #app{
    text-align: center;
    padding: 15px;
    background-image: linear-gradient(to right, rgba(5, 123,194, 0.5), rgba(24, 179, 32, 0.5));
  }
  img{
    background-color: white;
    border-radius: 25px;
    padding: 2px 10px;
  }
</style>
