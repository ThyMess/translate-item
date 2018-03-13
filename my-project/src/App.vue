<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class="text-muted">简单 / 易用 / 便捷</h5>
    <TranslateForm @formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/Translateform'
import TranslateOutput from './components/TranslateOutPut'
export default {
  name: 'App',
  data:function () {
    return {
      translatedText:""
    }
  },
  components: {
    TranslateForm,TranslateOutput
  },
  methods:{
    translateText:function (text,language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate' +
        '?key=trnsl.1.1.20180313T065712Z.36dc6a944214d45d.24238d638b91cc4a6f56dfbf90ce500ed0910c77' +
        '&lang='+language +
        '&text='+text)
        .then((response)=>{
          //console.log(response.body.text[0]);
          this.translatedText = response.body.text[0];
        })

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
