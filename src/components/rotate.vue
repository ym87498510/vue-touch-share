<!--需要注释meta中视口-->
<template>
  <div class="wrapper">
    <p>事件名称:{{eventName}}</p>
    <p>持续时间:{{deltaTime}}毫秒</p>
    <p>中心移动的距离:{{distance}}</p>
    <p>中心坐标x:{{pointX}}&nbsp;y:{{pointY}}</p>
    <p>缩放率{{scale}}</p>
    <!--角度明细暂时不能确定-->
    <p>角度:{{rotation}}</p>
    <p>捏合角度:{{angle}}</p>
    <!--可以绑定参数，threshold最小移动距离  v-bind:pan-options="{ direction: 'horizontal', threshold: 10 }"  -->
    <v-touch class="back" tag="div"
             @rotate="rotate"
    >捏我!
    </v-touch>
  </div>
</template>

<script>
  export default {
    name: 'rotate',
    data () {
      return {
        eventName: '',
        deltaTime: 0,
        pointX: 0,
        pointY: 0,
        distance: 0,
        scale: 1,
        rotation: 0,
        angle: 0
      }
    },
    methods: {
      rotate (event) {
        console.log(event)
        this.pointX = event.center.x
        this.pointY = event.center.y
        this.deltaTime = event.deltaTime
        this.eventName = event.type
        this.distance = parseInt(event.distance)
        this.scale = event.scale.toFixed(2)
        this.rotation = event.rotation.toFixed(2)
        this.angle = event.angle.toFixed(2)
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
    line-height: 5rem;
    background: #24b735;
  }
</style>
