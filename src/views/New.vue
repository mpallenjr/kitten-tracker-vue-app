<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p>Name:  <input type="text" v-model="newKitten.name"></p>
    <p>Age:  <input type="text" v-model="newKitten.age"></p>
    <p>Breed:  <input type="text" v-model="newKitten.breed"></p>
    <p>Notes:  <input type="text" v-model="newKitten.notes"></p>
    <p>Image_URL:  <input type="text" v-model="newKitten.image_url"></p>
    <button v-on:click="newKitten">Add Kitten</button>

  </div>
</template>

<style></style>

<script>
import axios from 'axios';
  export default {
    data: function () {
      return {
        message: "Welcome to Vue.js!",
      };
    },
    created: function () {},
    methods: {

      newKitten: function() {
        console.log('hello')
        axios.post("http://localhost:3000/kittens",
        {
          name: this.newKitten.name,
          age: this.newKitten.age,
          breed: this.newKitten.breed,
          image_url: this.newKitten.image_url,
          notes: this.newKitten.notes

        }).then(response => {
          console.log(response.data)
        })
      }
    },
  };
</script>