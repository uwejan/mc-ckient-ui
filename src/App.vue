<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld :msg="service_status"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
// MeshCentral
const SERVICE_NAME = 'meshagent'
let serviceInstance = require('./modules/service-manager').manager.getService(SERVICE_NAME); // This returns a service object for the named service, if it is found. Otherwise an exception is thrown.

export default {
  name: 'App',
  data(){
    return {
      service_status: null,
    }
  },
  components: {
    HelloWorld
  },
  mounted() {
    this.service_status = serviceInstance.isRunning()
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
