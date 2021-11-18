<template>
  <div class="home">

    <div v-for="kitten in kittens">
      <p> {{ kitten.name }} </p>
      <p> {{ kitten.age }} </p>
      <p> {{ kitten.breed }} </p>
      <img v-bind:src="kitten.image_url">
    </div>
  </div>
</template>

<style></style>

<script>
import axios from 'axios';
  export default {
    data: function () {
      return {
        kittens: []
      };
    },
    created: function () {
      this.indexKittens();
    },
    methods: {
      indexKittens: function() {
        console.log('hello')
        axios.get("http://localhost:3000/kittens").then(response => {
          console.log(response.data)
          this.kittens = response.data 
        })
      },
      
    },
  };
</script>