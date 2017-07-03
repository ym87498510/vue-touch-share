<template>
  <div class="wrapper" @touchmove="move">

  </div>
</template>

<script>
  export default {
    name: 'touchmove',
    methods: {
      move (event) {
        console.log(event)
      }
    }
  }
</script>

<style scoped>
.wrapper {
  box-sizing: border-box;
  width: 7.5rem;
  height: 7.5rem;
  border: 1px solid #666;
}
</style>
