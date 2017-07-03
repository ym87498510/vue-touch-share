<!--需要注释meta中视口-->
<template>
  <div class="wrapper">
    <p>事件名称:{{eventName}}</p>
    <p>持续时间:{{deltaTime}}毫秒</p>
    <p>距离:{{distance}}</p>
    <p>坐标x:{{pointX}}&nbsp;y:{{pointY}}</p>
    <!--可以绑定参数，threshold最小移动距离  v-bind:pan-options="{ direction: 'horizontal', threshold: 10 }"  -->
    <v-touch class="back" tag="div"
             @pan="pan"
    >Pan me!


    </v-touch>
  </div>
</template>

<script>
  export default {
    name: 'pan',
    data () {
      return {
        eventName: '',
        deltaTime: 0,
        pointX: 0,
        pointY: 0,
        distance: 0
      }
    },
    methods: {
      pan (event) {
        this.pointX = event.center.x
        this.pointY = event.center.y
        this.deltaTime = event.deltaTime
        this.eventName = event.type
        this.distance = parseInt(event.distance)
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .back {
    box-sizing: border-box;
    width: 7.5rem;
    height: 5rem;
    background: #24b735;
  }
</style>
