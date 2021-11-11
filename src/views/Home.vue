<template>
  <div class="home">
    <h1>hello</h1>
    <hr />
    <p>Name:<input type="text" v-model="newPhotos.name"></p>
    <p>Price:<input type="text" v-model="newPhotos.price"></p>
    <p>Description:<input type="text" v-model="newPhotos.description"/></p>
    <p>Image:<input type="text" v-model="newPhotos.image_url"/></p>
    <button v-on:click="createPhotos()">Create Action</button>

    <div v-for="photo in photos">
      <p>ID:{{ photo.id }}</p>
      <p>Name:{{ photo.name }}</p>
      <p>Price:{{ photo.price }}</p>
      <p>Description:{{ photo.description }}</p>
      <img v-bind:src="photo.image_url">
      <hr/>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
data: function() {
return {
  // where stuff goes in data
photos: [],
newPhotos: {}
};
},
created: function() {
  this.indexPhotos();

},
methods: {
  indexPhotos: function() {
axios.get("http://localhost:3000/photos").then(response => {
  console.log(response.data)
  this.photos = response.data
})
},

  createPhotos: function() {
    console.log('hello')
    axios.post("http://localhost:3000/photos",
    {
      name: this.newPhotos.name,
      price: this.newPhotos.price,
      description: this.newPhotos.description,
      image_url: this.newPhotos.image_url


    }).then(response => {
      console.log(response.data)
    })


  },

},
};

</script>

<style>

</style>