<template>
  <div>
    <div @click="close($event)">
    <h1>Stories from The Guardian API</h1>
    <div class='nav-bar'>
      <NavBar/>
    </div>
    <div class= 'feature-box'>
      <FeaturedArticle :article='this.article'/>
    </div>
    <div class='container'>
      <ul class='cards'>
        <li v-for="(item, index) in results">
          <StandardArticle :article='item'/>
        </li>
      </ul>
    </div>
  </div>
  </div>
</template>

<script>
import FeaturedArticle from './FeaturedArticle.vue';
import StandardArticle from './StandardArticle.vue';
import NavBar from './NavBar.vue';
import { eventBus } from '../main.js';

export default {
  name: 'HomePage',
  data(){
    return{
      results:[],
      article: [],
      searchValue:'software'
    }
  },
  components:{
    FeaturedArticle,
    StandardArticle,
    NavBar
  },

  methods:{
    getData(){
      fetch(`https://content.guardianapis.com/search?&show-tags=contributor&q=${this.searchValue}&show-blocks=all&api-key=d682a5ab-feca-4d46-b6c9-8507b8bd6efd`)
      .then(response => response.json())
      .then((data) => {
        this.results = data.response.results;
        // this.results.pop();
        this.article = this.results.shift()
      })
    },

    close(event){
      eventBus.$emit('close-modal')
    }
  },

  watch:{
    // any time the searchValue gets updated a new fetch will be triggered with the new search value
    searchValue: function(){
      this.getData()
    }
  },

  mounted(){
    this.getData()

    eventBus.$on('search-input', (value) => {
        this.searchValue = value;
    })
  }
}
</script>
<style>

.feature-box{
  margin: 0 auto;
  width: 70%;
  height: 350px;
}

ul{
  list-style-type: none;
}

li{
  padding: 10px;
}

.cards{
  padding-top: 100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-gap: 20px;
  align-items: center;
  width: 85%;
}

.nav-bar{
  margin: 0 auto;
}


</style>
