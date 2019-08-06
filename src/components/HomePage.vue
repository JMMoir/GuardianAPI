<template>
  <div>
    <h1>Stories from the Guardian API</h1>
    <div id='search'>
      <SearchBar/>
    </div>
    <div class= 'feature'>
      <FeaturedArticle :article='this.results[0]'/>
    </div>
    <div class='container'>
      <ul class='cards'>
        <li v-for="(item, index) in results">
          <StandardArticle :article='item'/>
        </li>
      </ul>
    </div>

  </div>
</template>

<script>
import FeaturedArticle from './FeaturedArticle.vue';
import StandardArticle from './StandardArticle.vue';
import SearchBar from './SearchBar.vue';
import { eventBus } from '../main.js';

export default {
  name: 'HomePage',
  data(){
    return{
      results:[],
      searchValue:'UK'
    }
  },
  components:{
    FeaturedArticle,
    StandardArticle,
    SearchBar
  },

  methods:{
    getData(){
      fetch(`https://content.guardianapis.com/search?&show-tags=contributor&q=${this.searchValue}&show-blocks=all&api-key=d682a5ab-feca-4d46-b6c9-8507b8bd6efd`)
      .then(response => response.json())
      .then((data) => {
        this.results = data.response.results;
      })
    }
  },

  watch:{
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

.feature{
  margin: 0 auto;
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
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  grid-gap: 20px;
  align-items: center;
  width: 900px;
}

#search{
  padding-bottom: 30px;
}

</style>
