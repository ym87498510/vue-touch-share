<!--需要注释meta中视口-->
<template>
  <div class="wrapper">
    <p>事件名称:{{eventName}}</p>
    <p>持续时间:{{deltaTime}}毫秒</p>
    <p>坐标x:{{pointX}}&nbsp;y:{{pointY}}</p>
    <v-touch class="back" tag="div"
             @tap="tap"
    >Tap me!
    </v-touch>
  </div>
</template>

<script>
  export default {
    name: 'tap',
    data () {
      return {
        eventName: '',
        deltaTime: 0,
        pointX: 0,
        pointY: 0
      }
    },
    methods: {
      tap (event) {
        this.pointX = event.center.x
        this.pointY = event.center.y
        this.deltaTime = event.deltaTime
        this.eventName = event.type
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .back {
    box-sizing: border-box;
    width: 7.5rem;
    height: 7.5rem;
    background: #24b735;
  }
</style>
