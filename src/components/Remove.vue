

<template>
  <div class='remove'>
    <br>
    <h2>Remove scheduled job</h2>
    <p>Are you sure you want to remove this job?</p>
    <input type='submit' @click='cancelRemove' value="Cancel" class='removeButton'></input>
    <input type='submit' @click='removeEverything'value="Remove Job" class='removeJobButton'></input>
  </div>
</template>


<script>
  export default {
    name: 'Remove',
    methods: {
      cancelRemove() {
        this.$parent.blackBackground = 0;
      },
      removeEverything() {
        // console.log('hi');
        // console.log(this.$parent.goneForever);
        this.$parent.goneForever = 0;
        console.log(this.$parent.$parent.$parent.keepHelloAlive -= 1);
      },
    },
    data() {
      return {
      };
    },
  };
</script>
