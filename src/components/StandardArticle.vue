<template lang="html">
  <div class = 'card'>
    <img :src="article.blocks.main.elements[0].assets[0].file"/>
    <div class='container'>
      <h3>{{article.webTitle}}</h3>
      <a :href="article.webUrl">View full Story</a>
  </div>
  </div>
</template>

<script>
export default {
  name: 'StandardArticle',
  props:['article']
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
</style>
