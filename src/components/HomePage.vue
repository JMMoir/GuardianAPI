<template>
  <div>
    <h1>Home</h1>
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

export default {
  name: 'HomePage',
  data(){
    return{
      results:[]
    }
  },
  components:{
    FeaturedArticle,
    StandardArticle,
    SearchBar
  },

  mounted(){

    fetch('https://content.guardianapis.com/search?&show-tags=contributor&q=boris&show-blocks=all&api-key=d682a5ab-feca-4d46-b6c9-8507b8bd6efd')
    .then(response => response.json())
    .then((data) => {
      this.results = data.response.results;
      console.log(this.results);
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
