<template>

  <div class = 'feature'>
    <img :src="article.blocks.main.elements[0].assets[0].file"/>
    <div>
      <h2>Featured Story</h2>
      <h3>{{article.webTitle}}</h3>
      <!-- <p>{{article.blocks.body[0].bodyTextSummary}}</p> -->
      <p>by: {{article.tags[0].webTitle}}</p>
      <!-- <p>{{article.blocks.main.elements[0].assets[0].file}}</p> -->
  </div>

  </div>
</template>

<script>
export default{
  name: 'FeaturedArticle',
  props:['article']
}
</script>

<style>

.feature{
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  width: 600px;
  height: 200px;
  overflow: hidden;
}

img {
  max-width: 100%;
  max-height: 100%;
  float: left;
}

</style>
