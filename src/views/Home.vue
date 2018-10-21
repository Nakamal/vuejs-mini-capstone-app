<template>
  <div class="home">
    <h1>{{ message }}</h1>
  </div>
</template>

<style>
</style>

<script>
var axios = require('axios');
export default {
  data: function() {
    return {
      message: "Winston's Wacky & Wonderous Items"
    };
  },
  created: function() {},
  methods: {},
  computed: {}
};
</script>