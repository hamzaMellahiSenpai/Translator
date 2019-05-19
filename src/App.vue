<template>
  <div id="app">
    <h2 class="py-5">Word Translator</h2>
    <TranslatorForm @formSubmit="translateText"></TranslatorForm>
    <Output v-text="translatedOutput"></Output>
  </div>
</template>

<script>
import TranslatorForm from './components/TranslatorForm.vue'
//import Output from "./components/Output.vue"

export default {
  name: 'app',
  components: {
    TranslatorForm,
    //Output
  },
  data: function(){
    return {
      translatedOutput:""
    }
  },
  methods: {
    translateText : function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170329T180255Z.3c18d2dc7b65d525.f23ed9a9efa992bded4ef96334e3c154f61d2dea&text=' + text + '&lang='+language)
          .then((response) => {
              this.translatedOutput = response.body.text[0];
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
