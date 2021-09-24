<template>
  <div class="container">
    <div class="container_row">
      <div class="container_item"><CounterBlock target="ドロップ数"/></div>
      <div class="container_item"><CounterBlock target="周回数"/></div>
    </div>
  </div>
  <div class="container_row"><StopWatch class="stopwatch"/></div>
</template>

<script>
import CounterBlock from './components/CounterBlock.vue'
import StopWatch from './components/StopWatch.vue'

export default {
  name: 'App',
  components: {
    CounterBlock,
    StopWatch
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
#app {
  font-family: 'メイリオ', Meiryo,'Hiragino Kaku Gothic ProN','ヒラギノ角ゴ ProN W3','ＭＳ Ｐゴシック','MS PGothic''MS UI Gothic','Helvetica','Arial',sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: auto;
}
.container {
  display: flex;
  flex-direction: column;
  margin: 0.5rem;
}
.container_row {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}
.container_item {
  margin: 5px;
  padding: auto;
}
</style>
