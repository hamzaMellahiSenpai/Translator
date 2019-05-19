<template>
  <div row ="row" class="TranslatorForm">
    <div class="col-md-6 col-md-offset-6 mx-auto my-4 jumbotron">
      <form action="" class="form-inline well" @submit.prevent="formSubmit">
        <input type="text" v-model="word" class="ml form-control" placeholder="type Someting.....">
        <select v-model="languageToTranslate" class="form-control">
          <option v-for="language in languages" v-bind:key="language.id" v-bind:value="language.ab">
            {{ language.name  }}
          </option>
        </select>
        <input type="submit" value="Translate" class="ml btn btn-danger">
      </form>
    </div>
  </div>
</template>
<script>

export default {
  name:"TranslatorForm",
  data(){
    return{
      word:"",
      languages:[
        {id:1, ab: "en", name:"english"},
        {id:2, ab: "ru", name:"russia"},
        {id:3, ab: "ar", name:"Arabic"},
        {id:4, ab: "es", name:"Spanish"}
      ],
      languageToTranslate:""
    }
  },
  // SELECT FRENSH AS DEFAULT LANGUAGE
  created(){
    this.languageToTranslate = "fr"
  },
  methods : {
    formSubmit(e){
      this.$emit('formSubmit', this.word, this.languageToTranslate);
      e.preventDefault();
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.ml {
    margin-left:30px
}
.jumbotron{
    box-shadow: 0px -1px 10px #F2F2F2;
}
</style>
