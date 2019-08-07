<template lang="html">
  <div class="container">
    <div class="modal">
      <div class="modal-body">
        <h3>{{article.webTitle}}</h3>
        <p>{{article.blocks.body[0].bodyTextSummary}}</p>
        <button type="button" class="btn" @click="close">Close</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props:["article"],

  methods:{
    close(){
      this.$emit('close')
    }
  }
}
</script>

<style lang="css" scoped>

.container {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    width: 600px;
    height:500px;
    overflow: scroll;
    box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  }

  .modal {
    background: white;

    overflow-x: auto;
    margin: auto;
  }

  .modal-body {
    padding: 20px;
  }

  .btn{
    border: 1px solid #4AAE9B;
    border-radius: 2px;
    cursor: pointer;
  }
</style>
