<template>
  <div>
    <p>Home</p>
    <FeaturedArticle :article='this.results[0]'/>
    <ul>
      <li v-for="(item, index) in results">
        <StandardArticle :article='item'/>
      </li>
    </ul>

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

    fetch('https://content.guardianapis.com/search?q=debate%20AND%20economy&tag=politics/politics&from-date=2014-01-01&api-key=d682a5ab-feca-4d46-b6c9-8507b8bd6efd')
    .then(response => response.json())
    .then((data) => {
      this.results = data.response.results;
    })
  }
}
</script>
