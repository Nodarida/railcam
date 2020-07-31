<template>
  <div id="app">
    <img alt="HfG-Logo" src="./assets/hfg.png">
    <Layout streamUrl='http://hal.hfg.design:50005/live-20680.mjpg'>
      <template v-slot:videocomponent></template>
        <template v-slot:controlcomponent>

            <controls></controls>
          </template>
          <template v-slot:queuecomponent><Queue/></template>
    </Layout>
  </div>
</template>


<script>
  import Controls from './components/control.vue';
  import Layout from './submodules/base_layout/src/components/interface.vue';
  import Queue from './components/SimpleQueueComponent.vue'

  export default {
    name: 'App',
    components: {
      Layout,
      Controls,
      Queue,
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