<template lang="html">
  <div class="search">
    <div class ="search-bar">
      <input class="bar" type=text v-model='searchValue' v-on:keydown.enter="handleSearchValue" placeholder="Search..."/>
    </div>
    <button class ="search-button" v-on:click="handleSearchValue"><i class="fa fa-search"></i></button>
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

.search{
  display:flex;
  justify-content: center;
  position: relative;
  width: 200px;
  margin:0 auto;
  border: 1px solid #4AAE9B;
  border-radius: 2px;
}
.search-bar{
  padding: 5px;
}

.bar{
  height: 20px;
  border-style: none;
  width: 140px;
}

.search-button{
  padding-top:10px;
  padding-right: 5px;
  height:20px;
  border-style: none;
  cursor: pointer;
}

.bar:focus{
  outline: none;
}

.search-button:focus{
  outline: none;
}


</style>
