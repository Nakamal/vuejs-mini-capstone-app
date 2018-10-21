<template>
  <div class="products-new">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>Create an Item</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Name:</label> 
          <input type="text" class="form-control" v-model="name">
        </div>
        <div class="form-group">
          <label>Description:</label>
          <input type="text" class="form-control" v-model="description">
        </div>
        <div class="form-group">
          <label>Rarity:</label>
          <input type="text" class="form-control" v-model="rarity">
        </div>
        <div class="form-group">
          <label>Cursed:</label>
          <input type="text" class="form-control" v-model="cursed">
        </div>
        <div class="form-group">
          <label>Image URL:</label>
          <input type="text" class="form-control" v-model="imageURL">
        </div>
        <input type="submit" class="btn btn-primary" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      name: "",
      description: "",
      rarity: "",
      imageURL: "",
      cursed: "",
      errors: []
    };
  },
  methods: {
    submit: function() {
      var params = {
        name: this.name,
        description: this.description,
        rarity: this.rarity,
        imageURL: this.imageURL,
        cursed: this.cursed
      };
      axios
        .post("http://localhost:3000/api/products", params)
        .then(response => {
          this.$router.push("/products/" + response.data.id);
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>