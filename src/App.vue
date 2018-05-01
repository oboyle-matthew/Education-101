<template>
  <div id="app">
    <p>Test</p>
    <People :black_num="black_num"
            :white_num="white_num">

    </People>

  </div>
</template>



<script>
  import People from './components/People.vue'
  
  export default {
  name: 'app',
  components: {
    People
  },
  data () {
    return {
      black_num: 5,
      white_num: 3
    }
  }
}
</script>

<style lang="scss">
</style>
