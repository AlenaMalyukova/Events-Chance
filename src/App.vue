<template>
  <div id="app">
    <EventsList />
  </div>
</template>

<script>
import EventsList from './components/EventsList.vue'
export default {
  name: 'App',
  components: {
    EventsList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
