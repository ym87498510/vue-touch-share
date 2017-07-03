<template>
  <transition name="move">
    <v-touch tag="div" class="switch" :class="{active: active}" @tap="toggle" @panleft="off" @panright="on">
      <div class="handle"></div>
    </v-touch>
  </transition>
</template>

<script>
  export default {
    name: 'onOff',
    data () {
      return {
        active: false
      }
    },
    methods: {
      toggle () {
        this.active = !this.active
      },
      off () {
        this.active = false
      },
      on () {
        this.active = true
      }
    }
  }
</script>

<style scoped>
  .switch {
    width: 2rem;
    height: 1.2rem;
    margin: 0 auto;
    background: #fff;
    border-radius: 1rem;
    border: 3px solid #c8c8c8;
    overflow: hidden;
    transition: all 0.2s linear;
  }

  .handle {
    width: 1.2rem;
    height: 1.2rem;
    background: #fff;
    border-radius: 50%;
    box-shadow: 4px 4px 8px rgba(0, 0, 0, 0.16);
    transition: all 0.2s linear;
  }

  .switch.active {
    background: #23beae;
    border: 3px solid #23beae;
  }

  .switch.active .handle {
    box-shadow: 0 0 0 rgba(255, 255, 255, 0);
    transform: translate3D(0.8rem, 0, 0);
  }
</style>
