<template>
  <div class="home">
    <div>
      <h1>hello</h1>
      <p>{{ photos }}</p>
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
console.log('hello')
axios.get("http://localhost:3000/photos").then(response => {
  console.log(response.data)
} )

  },

},
};

</script>

<style>

</style>