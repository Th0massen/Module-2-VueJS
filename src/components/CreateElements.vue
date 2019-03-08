<template>
    <div class="Element">
        <h2>{{ title }}</h2>
        <img :src="thumbnail" alt="Thumbnail Image"/><br/>
        <p>Ingredients :</p>
        <p class="ingredients">{{ ingredients }}</p>
        <br/>
        <span>Go to:</span><a :href="href">{{ title }}</a>
    </div>    
</template>

<script>
export default {
    name: 'Recipe',
    props: {
        title: String,
        href: String,
        thumbnail: String,
        ingredients: String,
        DataList: []
    }
}
</script>

<style scoped>
.Element{
    margin: 35px auto;
    padding: 5px;
    width: 350px;
    border: 0.5px solid black;
    box-shadow: 2px 2px 15px 2px;
    background-color: white;
}
h2{
    border-bottom: 0.5px solid black;
}
p{ 
    padding: 5px 20px;
    font-size: 18px;
}
a{
    margin: 10px;
}
img{
    width: 100px;
    height: auto;
}
</style>
