<template>
  <div id="translateOutput" class="mTop">
    <h2 class="mTop">{{translatedText}}</h2>
  </div>
</template>

<script>
    export default {
        name: "translateOutput",
      props:[
        "translatedText"
      ]
    }
</script>

<style scoped>
  .mTop{
    margin-top: 50px;
  }
</style>
