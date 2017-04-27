<template>
  <div id="app">
    <hello></hello>
    <!--<Created></Created>-->
    <br>
    <Create></Create>
  </div>
</template>

<script>
import Hello from './components/Hello';
import Create from './components/Create';
// import Created from './components/Created';

export default {
  name: 'app',
  data() {
    return {
    };
  },
  methods: {

  },
  components: {
    Hello,
    Create,
    // Created,
  },
  created() {
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
