<template>
  <div id="app">
    <hello v-if='keepHelloAlive === 1'></hello>
    <br>
    <Create></Create>
  </div>
</template>

<script>
import Hello from './components/Hello';
import Create from './components/Create';

export default {
  name: 'app',
  data() {
    return {
      keepHelloAlive: 1,
    };
  },
  methods: {
  },
  components: {
    Hello,
    Create,
  },
};
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
