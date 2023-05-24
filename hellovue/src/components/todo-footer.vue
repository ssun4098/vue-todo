<template>
  <h1>{{message}}</h1>
  <h1>{{footerName}}</h1>
  <button v-on:click="showLog"></button>
  <button v-on:click="testMitt">Mitt</button>
</template>

<script>

export default {
  name: "todo-footer",
  data: function () {
    return {
      message: "todo-footer123"
    }
  },
  props: [
    'footerName'
  ],
  methods: {
    showLog: function () {
      this.$emit('show-log');
    },
    testMitt: function () {
      this.emitter.emit("addEvent", "message")
    }
  }
}
</script>

<style scoped>

</style>