<template>
  <div id="app">
    <!--测试点击延迟-->
    <!--<click-delay></click-delay>-->
    <!--测试点透bug-->
    <!--<click-bug></click-bug>-->
    <!--看看都有哪些事件-->
    <!--<events></events>-->
    <!--<tap></tap>-->
    <!--<pan></pan>-->
    <!--<swiper></swiper>-->
    <!--<pinch></pinch>-->
    <rotate></rotate>
  </div>
</template>

<script>
import clickBug from './components/clickBug'
import events from './components/events'
import clickDelay from './components/clickDelay'
import tap from './components/tap'
import pan from './components/pan'
import swiper from './components/swiper'
import pinch from './components/pinch'
import rotate from './components/rotate'

export default {
  name: 'app',
  components: {
    clickBug,
    clickDelay,
    events,
    tap,
    pan,
    swiper,
    pinch,
    rotate
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  font-size: .5rem;
}
</style>
