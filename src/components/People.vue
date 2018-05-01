<template>
  <div id="app">
    <p>{{black_num}}</p>
    <p>{{white_num}}</p>
  </div>
</template>

<script>
  export default {
    name: 'app',
    props: ['black_num', 'white_num'],
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    }
  }
</script>

<style lang="scss">
</style>
