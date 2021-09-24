<template>
  <div class="elm">{{ target }}</div>
  <BaseButton class="elm" indication="+" :handleClickEvent="addCount"/>
  <div><input class="elm count" type="tel" v-model.number="count"></div>
  <BaseButton class="elm" indication="-" :handleClickEvent="minusCount"/>
</template>

<script>
import BaseButton from './BaseButton.vue'

export default {
  name: 'CounterBlock',
  components: {
    BaseButton
  },
  props: {
    target: String
  },
  data() {
    return {
      count: 0
    }
  },
  methods: {
    addCount(){
      this.count += 1;
    },
    minusCount(){
      this.count -= 1;
    }
  }
}
</script>

<style>
.elm {
  margin: auto;
  padding: auto;
  width: 5rem;
  height: 2rem;
}
.count {
  font-size: 1em;
}
.button {
  width: 3rem;
}
</style>