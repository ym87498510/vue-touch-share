<template>
  <div class="wrapper">
    <p>eventName:{{eventName}}</p>
    <v-touch class="back" tag="div"
             @rotate="rotate"
             @tap="tap"
             @rotatestart="rotatestart"
             @rotatemove="rotatemove"
             @rotateend="rotateend"
             @rotatecancel="rotatecancel"
             @swipeleft="swipeleft"
             @swiperight="swiperight"
             @swipeup="swipeup"
             @swipedown="swipedown"
             @press="press"
             @pressup="pressup"
             @pinch="pinch"
             @pinchin="pinchin"
             @pinchout="pinchout"
             @panleft="panleft"
             @panright="panright"
             @panup="panup"
             @pandown="pandown"
    >Touch me!
    </v-touch>
  </div>
</template>

<script>
  export default {
    name: 'events',
    data () {
      return {
        eventName: ''
      }
    },
    methods: {
      tap (event) {
        console.log(event)
        this.eventName = 'tap'
      },
      rotate (event) {
        console.log(event)
        this.eventName = 'rotate'
      },
      rotatestart (event) {
        console.log(event)
        this.eventName = 'rotatestart'
      },
      rotatemove (event) {
        console.log(event)
        this.eventName = 'rotatemove'
      },
      rotateend (event) {
        console.log(event)
        this.eventName = 'rotateend'
      },
      rotatecancel (event) {
        console.log(event)
        this.eventName = 'rotatecancel'
      },
      swipeleft (event) {
        console.log(event)
        this.eventName = 'swipeleft'
      },
      swiperight (event) {
        console.log(event.deltaY)
        this.eventName = 'swiperight'
      },
      swipeup (event) {
        console.log(event.deltaY)
        this.eventName = 'swipeup'
      },
      swipedown (event) {
        console.log(event.deltaY)
        this.eventName = 'swipedown'
      },
      press (event) {
        console.log(event)
        this.eventName = 'press'
      },
      pressup (event) {
        console.log(event)
        this.eventName = 'pressup'
      },
      pinch (event) {
        console.log(event)
        this.eventName = 'pinch'
      },
      pinchin (event) {
        console.log(event.distance, event.pointers[0].clientX, event.pointers[0].clientY, event.pointers[1].clientX, event.pointers[1].clientY)
        this.eventName = 'pinchin'
      },
      pinchout (event) {
        console.log(event)
        this.eventName = 'pinchout'
      },
      panleft (event) {
        console.log(event)
        this.eventName = 'panleft'
      },
      panright (event) {
        console.log(event)
        this.eventName = 'panright'
      },
      panup (event) {
        console.log(event)
        this.eventName = 'panup'
      },
      pandown (event) {
        console.log(event)
        this.eventName = 'pandown'
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .back {
    position: relative;
    box-sizing: border-box;
    width: 7.5rem;
    height: 7.5rem;
    background: #24b735;
  }
</style>
