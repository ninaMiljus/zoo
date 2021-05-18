<template>
  <div id="app">
    <div class="container">
      <AnimalList msg="Welcome to Your Vue.js App"/>
    </div>
  </div>
</template>

<script>
import AnimalList from './components/AnimalList.vue'

export default {
  name: 'App',
  components: {
     AnimalList
  }
}
</script>


