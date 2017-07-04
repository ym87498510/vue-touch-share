<template>
  <div class="wrapper">
    <p>事件名称:{{eventName}}</p>
    <p>持续时间:{{deltaTime}}毫秒</p>
    <p>中心移动的距离:{{distance}}</p>
    <p>中心坐标x:{{pointX}}&nbsp;y:{{pointY}}</p>
    <p>缩放率{{scale}}</p>
    <!--可以绑定参数，threshold最小移动距离  v-bind:pan-options="{ direction: 'horizontal', threshold: 10 }"  -->
    <v-touch class="back" tag="div"
             @pinch="pinch"
    >
      <img ref="pic" src="../assets/oh.jpeg">
    </v-touch>
  </div>
</template>

<script>
  export default {
    name: 'pinch',
    data () {
      return {
        eventName: '',
        deltaTime: 0,
        pointX: 0,
        pointY: 0,
        distance: 0,
        scale: 1,
        picWidth: null
      }
    },
    mounted () {
      this.setWidth()
    },
    methods: {
      pinch (event) {
        this.pointX = event.center.x
        this.pointY = event.center.y
        this.deltaTime = event.deltaTime
        this.eventName = event.type
        this.distance = parseInt(event.distance)
        this.scale = event.scale.toFixed(2)
        this.rotation = event.rotation.toFixed(2)
        this.angle = event.angle.toFixed(2)
        this.$refs.pic.style.width = parseInt(this.picWidth) * event.scale + 'px'
        if (event.isFinal) {
          this.setWidth()
        }
      },
      setWidth () {
        console.log('setWidth')
        this.picWidth = window.getComputedStyle(this.$refs.pic).width
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
    border: 5px solid #888;
    display: flex;
    overflow: hidden;
    justify-content: center;
    align-items: center;
  }
  img {
    width: 7.5rem;
    min-width: 1rem;
  }
</style>
