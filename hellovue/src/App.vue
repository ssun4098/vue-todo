<template>
  <h1>App.vue</h1>
  <a v-if="flag">두잇 Vue.js</a>
  <ul>
    <li v-for="system in systems" v-bind:key="system">{{system}}</li>
  </ul>
  <p v-show="flag">두잇</p>
  <h5 v-bind:id="uid">뷰 입문서</h5>
  <button v-on:click="popupAlert">경고창 버튼</button>
</template>

<script>
  export default {
    data: function () {
      return {
        flag: true,
        systems: ['android', 'ios', 'window'],
        uid: 10
      }
    },
    methods: {
      popupAlert: function () {
        return alert(this.uid);
      }
    }
  }
</script>

<style scoped>

</style>
