<template v-if="props">
  <div class = 'card'>
    <img :src="article.blocks.main.elements[0].assets[0].file"/>
    <div class='container'>
      <h3>{{article.webTitle}}</h3>
      <button type='button' class='btn' @click="showModal">View article</button>
      <modal v-show="modalIsVisible" @close="hideModal" :article="article"/>
  </div>
  </div>
</template>

<script>
import Modal from './Modal.vue';
export default {
  name: 'StandardArticle',
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

<style lang="css" scoped>

.card{
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
}

.container {
  padding: 2px 16px;
}
a{
  text-decoration: none;
}

img{
  width: 100%;
  height: 100%;
}

.btn{
  border: 1px solid #4AAE9B;
  border-radius: 2px;
  cursor: pointer;
}
</style>
