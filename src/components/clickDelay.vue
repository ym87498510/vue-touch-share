<!--需要注释meta中视口-->
<template>
  <div class="wrapper">
    <p>{{time1}}</p>
    <p>{{time2}}</p>
    <!--click事件没有触发-->
    <!--<v-touch class="middle" tag="div" @tap="tapEvent" @click="clickEvent">Tap me!</v-touch>-->
    <div class="middle" @touchstart="tapEvent" @click="clickEvent">点我</div>
  </div>
</template>

<script>
  export default {
    name: 'clickDelay',
    data () {
      return {
        time1: 'tap没有触发',
        time2: '点击没有触发'
      }
    },
    methods: {
      clickEvent () {
        this.time2 = '点击时间' + new Date().getTime()
      },
      tapEvent () {
        this.time1 = 'tap时间' + new Date().getTime()
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

  .middle{
    position: absolute;
    left: 0;
    top: 1rem;
    width: 4rem;
    height: 4rem;
    z-index: 2;
    background: blue;
  }

</style>
