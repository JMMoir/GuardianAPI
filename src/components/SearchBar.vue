<template lang="html">
  <div>
    <input type=text v-model='searchValue'/>
    <button v-on:click="handleSearchValue">Search</button>
  </div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
  name: 'SearchBar',

  data(){
    return{
      searchValue:''
    }
  },
  methods:{
    handleSearchValue(event){
      eventBus.$emit('search-input', this.searchValue)
      this.searchValue = ''
    }
  }
}

</script>

<style lang="css" scoped>
</style>
