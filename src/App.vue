<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Layout> 
      <template v-slot:controlcomponent> <controls></controls> </template>
    </Layout>
  </div>
</template>


<script>
import Controls from './components/control.vue';
import Layout from './submodules/base_layout/src/components/interface.vue';

export default {
  name: 'App',
  components: {
    Layout,
    Controls
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
  margin-top: 60px;
}


</style>
