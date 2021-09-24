<template>
<button class="button" @click="clickEvent()">{{ indication }}</button>
</template>

<script>
export default {
  name: 'BaseButton',
  props: {
    indication: String,
    handleClickEvent: {
        type: Function,
        required: true
    }
  },
  methods: {
    clickEvent() {
      this.handleClickEvent()
    }
  }
}
</script>