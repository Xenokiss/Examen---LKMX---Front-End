<template>
  <center>
    <div>
      <HelloWorld msg="LKMX - Front-End"/>
      <List/>
    </div>
  </center>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import List from './components/List.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,List
  }
}
</script>

<style>
body{
  background-color: #D4D4D4;
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
