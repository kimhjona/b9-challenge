<template>
  <div>
    <ul style='list-style-type: none;'>
      <li v-for='n in list'>
        <createTask></createTask>
      </li>
    </ul>
  </div>
</template>

<script>
import createTask from './createTask';

export default {
  name: 'Create',
  data() {
    return {
      list: 1,
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
    createTask,
  },
};
</script>
