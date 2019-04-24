<template>
  <div id="app">
   <h1>Word Translator</h1>
   <h5>powered By Vue.js</h5>
   <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
   <TranslateOutput v-text="translatedText" ></TranslateOutput>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

export default {
  name: 'app',
  components:{
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190424T120728Z.f61ae1067bb9686e.7dc12ae4a84c72db6abb189d88716d5dc6f9182d&lang='+language+'&text='+text).then((response) => {
        this.translatedText = response.body.text[0];
      })
    }
  }
}
</script>

<style>
#app {
 
}
</style>
