<template>
  <!--<addJob @click.native="clickJob" v-if="add"></addJob>-->
  <createTask v-else></createTask> 
</template>

<script>
import createTask from './createTask';
// import addJob from './addJob';

export default {
  name: 'Create',
  data() {
    return {
      // add: true,
    };
  },
  methods: {
    clickJob() {
      this.add = false;
    },
    clickBack() {
      this.add = true;
    },
  },
  components: {
    // addJob,
    createTask,
  },
};
</script>
