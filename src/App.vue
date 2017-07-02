<template>
  <div id="app">
    <!--测试点击延迟-->
    <!--<click-delay></click-delay>-->
    <!--测试点透bug-->
    <!--<click-bug></click-bug>-->
    <!--看看都有哪些事件-->
    <events></events>
  </div>
</template>

<script>
import clickBug from './components/clickBug'
import events from './components/events'
import clickDelay from './components/clickDelay'

export default {
  name: 'app',
  components: {
    clickBug,
    clickDelay,
    events
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
