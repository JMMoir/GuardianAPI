<template v-if="props">

  <div class = 'feature'>
    <img :src="article.blocks.main.elements[0].assets[0].file"/>
    <div>
      <h2>Featured Story</h2>
      <h3>{{article.webTitle}}</h3>

      <p>by: {{article.tags[0].webTitle}}</p>
      <!-- <a :href="article.webUrl">View full Story</a> -->
      <button type='button' class='btn' @click="showModal">View article</button>
      <modal v-show="modalIsVisible" @close="hideModal" :article="article"/>
      <!-- <p slot="body">{{article.blocks.body[0].bodyTextSummary}}</p> -->
  </div>

  </div>
</template>

<script>
import Modal from './Modal.vue'
export default{
  name: 'FeaturedArticle',
  props:['article'],
  components:{
    Modal
  },
  data(){
    return{
      modalIsVisible: false
    }
  },
  methods:{
    showModal(){
      this.modalIsVisible = true;
    },
    hideModal(){
      this.modalIsVisible = false;
    }
  }
}
</script>

<style>

.feature{
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  width: 750px;
  height: 250px;
  overflow: hidden;
}

img {
  max-width: 100%;
  max-height: 100%;
  float: left;
}

a{
  text-decoration: none;
}

.btn{
  border: 1px solid #4AAE9B;
  border-radius: 2px;
}

</style>
