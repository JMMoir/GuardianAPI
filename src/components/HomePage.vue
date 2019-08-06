<template>
  <div>
    <h1>Latest Stories</h1>
    <SearchBar/>
    <div>
      <FeaturedArticle :article='this.results[0]'/>
    </div>
    <div class='cards'>
      <ul>
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
      searchValue:'riots hong kong'
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
ul{
  display: inline-flex;
  list-style-type: none;
}

li{
  padding: 10px;
}
.cards {
display: grid;
grid-template-columns: 80px 80px;
grid-auto-rows: auto;
grid-gap: 10px;
padding: 10px;

}
</style>
