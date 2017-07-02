<!--需要注释meta中视口-->
<template>
  <div class="wrapper">
    <p>{{time1}}</p>
    <p>{{time2}}</p>
    <div v-show="backShow" class="back" @click="hideBack">Click Me!</div>
    <v-touch class="middle" v-if="middleShow" tag="div" @tap="hideMiddle">Tap me!</v-touch>
    <v-touch class="front" v-if="frontShow" tag="div" @tap="hideFront">Tap me!</v-touch>
  </div>
</template>

<script>
  export default {
    name: 'touch',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App',
        backShow: true,
        middleShow: true,
        frontShow: true,
        time1: '',
        time2: ''
      }
    },
    methods: {
      hideBack () {
        this.backShow = false
        this.time2 = '点击时间' + new Date().getTime()
      },
      hideMiddle () {
        this.middleShow = false
        this.time1 = 'tap时间' + new Date().getTime()
      },
      hideFront () {
        this.frontShow = false
        console.log(new Date().getTime())
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .wrapper {
    position: relative;
    box-sizing: border-box;
    width: 7.5rem;
    height: 7.5rem;
    border: 1px solid #ddd;
  }

  .back {
    position: absolute;
    left: 0;
    top: 1rem;
    width: 5rem;
    height: 5rem;
    z-index: 1;
    background: #666;
  }

  .middle{
    position: absolute;
    left: 0;
    top: 1rem;
    width: 4rem;
    height: 4rem;
    z-index: 2;
    background: blue;
  }

  .front {
    position: absolute;
    left: 0;
    top: 1rem;
    width: 3rem;
    height: 3rem;
    z-index: 3;
    background: green;
  }
</style>
