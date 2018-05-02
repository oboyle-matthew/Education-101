<template>
  <div id="app">
    <p>White = {{white_num.toFixed(2)}}%</p>
    <div class="horizontal" v-for="n in Math.floor(white_num)">
      <img src="https://thumbs.dreamstime.com/b/man-icon-vector-person-symbol-pictogram-illustration-glyph-97085462.jpg">
    </div>
    <p>Black = {{black_num.toFixed(2)}}%</p>
    <div class="horizontal" v-for="n in Math.floor(black_num)">
      <img src="https://thumbs.dreamstime.com/b/man-icon-vector-person-symbol-pictogram-illustration-glyph-97085462.jpg">
    </div>
    <p>Hispanic = {{hispanic_num.toFixed(2)}}%</p>
    <div class="horizontal" v-for="n in Math.floor(hispanic_num)">
      <img src="https://thumbs.dreamstime.com/b/man-icon-vector-person-symbol-pictogram-illustration-glyph-97085462.jpg">
    </div>
    <p>Asian = {{asian_num.toFixed(2)}}%</p>
    <div class="horizontal" v-for="n in Math.floor(asian_num)">
      <img src="https://thumbs.dreamstime.com/b/man-icon-vector-person-symbol-pictogram-illustration-glyph-97085462.jpg">
    </div>
  </div>
</template>

<script>
  export default {
    name: 'app',
    props: ['white', 'black', 'hispanic', 'asian'],
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },
    computed: {
      white_num: function() {
        return this.white / (this.white + this.black + this.hispanic + this.asian) * 100;
      },
      black_num: function() {
        return this.black / (this.white + this.black + this.hispanic + this.asian) * 100;
      },
      hispanic_num: function() {
        return this.hispanic / (this.white + this.black + this.hispanic + this.asian) * 100;
      },
      asian_num: function() {
        return this.asian / (this.white + this.black + this.hispanic + this.asian) * 100;
      }
    }
  }
</script>

<style lang="scss">
  .horizontal {
    display: inline;
  }

  img {
    width: 50px;
    height: 50px;
  }
</style>
