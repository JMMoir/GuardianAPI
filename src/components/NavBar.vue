<template lang="html">
  <div class='container'>
    <div>
      <ul class='nav-bar'>
        <li @click="handleBusiness">Business</li>
        <li @click="handlePolitics">Politics</li>
        <li @click="handleTechnology">Technology</li>
        <li id="search"><SearchBar/></li>
      </ul>
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
    }
  }
}
</script>

<style lang="css" scoped>

.nav-bar{
  display: flex;
  justify-content: flex-start;
}

.container{
  padding-bottom: 30px;
  margin: 0 auto;
  width: 750px;
}

li{
 cursor: pointer;
}

</style>
