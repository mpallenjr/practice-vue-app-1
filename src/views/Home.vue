<template>
  <div class="home">
    <h1>hello</h1>
    <hr />
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
photos: []
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
    axios.post("http://localhost:3000/photos").then(response => {
      console.log(response.data)
    })


  },

},
};

</script>

<style>

</style>