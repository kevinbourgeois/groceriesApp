<template>
  <the-header></the-header>
  <FormGroceries></FormGroceries>

</template>

<script>

import FormGroceries from './components/FormGroceries';
import TheHeader from "@/components/TheHeader";


export default {
  name: 'App',
  components: {
    TheHeader,
    FormGroceries
  },
  setup() {

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
body {
  margin: 0;
}
</style>
