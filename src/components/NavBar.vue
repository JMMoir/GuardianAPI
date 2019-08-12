<template lang="html">
  <div class='container'>
    <div>
      <ul class='nav-bar'>
        <li @click="handleUK">UK</li>
        <li @click="handleEurope">Europe</li>
        <li @click="handleBusiness">Business</li>
        <li @click="handlePolitics">Politics</li>
        <li @click="handleTechnology">Technology</li>
      </ul>
    </div>
    <div class='search'>
      <SearchBar/>
    </div>
  </div>
</template>

<script>
import SearchBar from './SearchBar.vue';
import { eventBus } from '../main.js'
export default {
  name:'NavBar',
  components:{
    SearchBar
  },

  methods:{
    handleBusiness(event){
      eventBus.$emit('search-input', 'Business')
    },
    handlePolitics(event){
      eventBus.$emit('search-input', 'politics')
    },
    handleTechnology(event){
      eventBus.$emit('search-input', 'Technology')
    },
    handleUK(event){
      eventBus.$emit('search-input', 'UK')
    },
    handleEurope(event){
      eventBus.$emit('search-input', 'Europe')
    }
  }
}
</script>

<style lang="css" scoped>

.nav-bar{
  display: flex;
  margin: 0 auto;
}

.container{
  padding-bottom: 30px;
  margin: 0 auto;
  width: 90%;
  display: flex;
}

li{
 cursor: pointer;
}

.search{
  margin-left: 90%;

}

</style>
