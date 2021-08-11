<template>
  <v-app id="dayspan" v-cloak>

  </v-app>
</template>

<script>
import Vue from 'vue';


export default {

  name: 'app',

  data: () => ({
   
  }),

  mounted()
  {
    window.app = this.$refs.app;

    this.loadState();
  },

  methods:
  {
    
  }
}
</script>

<style>


</style>
