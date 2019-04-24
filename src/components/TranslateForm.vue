<template>
  <div class="row" id="translateForm">
   <form class="well" v-on:submit="formSubmit">
    <input type="text" v-model="textToTranslate" placeholder="Enter a word...">
    <select v-model="language">
      <option value="ru">Russian</option>
      <option value="es">Spanish</option>
      <option value="fr">French</option>
      <option value="zh">Chinese</option>

    </select>
    <input type="submit" value="Translate">
   </form>
  </div>
</template>

<script>
export default {
  name: 'translateForm',
  data() {
    return {
      textToTranslate:'',
      language:''
    }
  },
  created() {
    this.language = 'zh';
  },
  methods: {
    formSubmit(e){
      // alert(this.textToTranslate);
      this.$emit('formSubmit', this.textToTranslate,this.language);
      e.preventDefault(); 
    }
  } 
}
</script>

<style>

</style>
