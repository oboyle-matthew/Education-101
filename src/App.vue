<template>
  <div id="app">
    <h1>Filter the data below!</h1>
    <button @click="filter = 'type'">Severity of punishment</button>
    <button @click="filter = 'gender'">Gender</button>
    <button @click="filter = 'poverty'">Poverty</button>



    <div v-if="filter === 'type'">
      <h3>Type of disciplinary action</h3>
      <input type="checkbox" value="0" v-model="type_filter">In school
      <input type="checkbox" value="1" v-model="type_filter">Out of school single
      <input type="checkbox" value="2" v-model="type_filter">Out of school multiple
      <input type="checkbox" value="3" v-model="type_filter">Expulsion
    </div>
    <div v-if="filter === 'gender'">
      <h3>Gender</h3>
      <input type="checkbox" value="0" v-model="gender_filter">Male
      <input type="checkbox" value="1" v-model="gender_filter">Female
    </div>
    <div v-if="filter === 'poverty'">
      <h3>Type of disciplinary action</h3>
      <input type="radio" value="0" v-model="poverty_filter">0-24%
      <input type="radio" value="1" v-model="poverty_filter">25-49%
      <input type="radio" value="2" v-model="poverty_filter">50-74%
      <input type="radio" value="3" v-model="poverty_filter">75-100%
    </div>
    <People :white="white"
            :black="black"
            :hispanic="hispanic"
            :asian="asian">
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
      enroll: [51,16,24, 5],
      inschool: [40, 32, 22,1],
      oossingle: [36,33,23,2],
      oosmultiple: [31, 42, 21, 1],
      expulsion: [36, 34, 22, 1],
      oosmalepercentage: [6,20,9,3],
      oosfemalepercentage: [2,12,4,1],
      preschoolsingle: [28, 42, 25, 1],
      preschoolmultiple: [26,48,20,1],
      first: [-13.7, 12.2, 4.4, -5.1],
      second: [-14.2, 14.0, 0.8, -2.6],
      third: [-13.7, 19.5, -5.0, -2.3],
      fourth: [-3.2, 24.6, -20.2, -2.0],
      type_filter: ['0', '1', '2', '3'],
      gender_filter: ['0', '1'],
      poverty_filter: '',
      filter: ''
    }
  },
    computed: {
    total_type: function() {
      return [this.inschool, this.oossingle, this.oosmultiple, this.expulsion]
    },
      total_gender: function() {
      return [this.oosmalepercentage, this.oosfemalepercentage];
      },
      total_poverty: function() {
      return [this.first, this.second, this.third, this.fourth];
      },
    white: function() {
      if (this.filter === 'type') {
        if (this.type_filter.length > 0) {
          var ans = 0;
          this.type_filter.forEach(num => ans += this.total_type[num][0]);
          ans = ans / this.type_filter.length;
          return ans / this.enroll[0]
        } else {
          return 0;
        }
      } else if (this.filter === 'gender') {
        if (this.gender_filter.length > 0) {
          var ans = 0;
          this.gender_filter.forEach(num => ans += this.total_gender[num][0]);
          return ans;
        } else {
          return 0;
        }
      } else if (this.filter === 'poverty') {
        if (this.poverty_filter.length > 0) {
          return (30 + this.total_poverty[this.poverty_filter][0]) * 10;
        } else {
          return 0;
        }
      }

    },
      black: function() {
        if (this.filter === 'type') {
          if (this.type_filter.length > 0) {
            var ans = 0;
            this.type_filter.forEach(num => ans += this.total_type[num][1]);
            ans = ans / this.type_filter.length;
            return ans / this.enroll[1]
          } else {
            return 0;
          }
        } else if (this.filter === 'gender') {
          if (this.gender_filter.length > 0) {
            var ans = 0;
            this.gender_filter.forEach(num => ans += this.total_gender[num][1]);
            return ans;
          } else {
            return 0;
          }
        } else if (this.filter === 'poverty') {
          if (this.poverty_filter.length > 0) {
            return (30 + this.total_poverty[this.poverty_filter][1]) * 8;
          } else {
            return 0;
          }
        }
      },
      hispanic: function() {
        if (this.filter === 'type') {
          if (this.type_filter.length > 0) {
            var ans = 0;
            this.type_filter.forEach(num => ans += this.total_type[num][2]);
            ans = ans / this.type_filter.length;
            return ans / this.enroll[2]
          } else {
            return 0;
          }
        } else if (this.filter === 'gender') {
          if (this.gender_filter.length > 0) {
            var ans = 0;
            this.gender_filter.forEach(num => ans += this.total_gender[num][2]);
            return ans;
          } else {
            return 0;
          }
        } else if (this.filter === 'poverty') {
          if (this.poverty_filter.length > 0) {
            return (30 + this.total_poverty[this.poverty_filter][2]) * 7.5;
          } else {
            return 0;
          }
        }
      },
      asian: function() {
        if (this.filter === 'type') {
          if (this.type_filter.length > 0) {
            var ans = 0;
            this.type_filter.forEach(num => ans += this.total_type[num][3]);
            ans = ans / this.type_filter.length;
            return ans / this.enroll[3]
          } else {
            return 0;
          }
        } else if (this.filter === 'gender') {
          if (this.gender_filter.length > 0) {
            var ans = 0;
            this.gender_filter.forEach(num => ans += this.total_gender[num][3]);
            return ans;
          } else {
            return 0;
          }
        } else if (this.filter === 'poverty') {
          if (this.poverty_filter.length > 0) {
            return (30 + this.total_poverty[this.poverty_filter][3]) * 5.5;
          } else {
            return 0;
          }
        }
      },
    }
}
</script>

<style lang="scss">
</style>
