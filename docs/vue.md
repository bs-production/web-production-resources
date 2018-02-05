# <i class="fab fa-vuejs"></i> Vue
***
### Playground
<vuep template="#example"></vuep>

<script v-pre type="text/x-template" id="example">
<style>
  .main {
    color: #fff;
  }
  .text {
    color: #4fc08d;
  }
</style>

<template>
  <div class="main">
    <h2> Do you even <span class="text">{{ name }}</span>?</h2>
    <h2>Features</h2>
    <ul>
      <li v-for="text in features">{{ text }}</li>
    </ul>
  </div>
</template>

<script>
  module.exports = {
    data () {
      return {
        name: 'Vue',
        features: [
          'Single File Component',
          'Babel for ES6/JSX/UMD/CommonJS',
          'Scoped style',
          'Customizable JavaScript scope'
        ]
      }
    }
  }
</script>
</script>

***
### Resources
[Vue Docs](https://vuejs.org/v2/guide/)  
[Vuetify - Material Component Framework](https://vuetifyjs.com/)  
[Buefy - Lightweight UI components for Vue.js based on Bulma](https://buefy.github.io/#/)  
[VeeValidate - Simple Vuejs Input Validation](http://vee-validate.logaretm.com/)  
[Nuxt - Universal Vue.js Applications](https://nuxtjs.org/)

### Projects using Vue.js
[Email Signature Generator](https://github.com/chrisroselli/email-signature-generator)

### Learn Vue.js
[Laracasts - Learn Vue 2: Step By Step](https://laracasts.com/series/learn-vue-2-step-by-step)  


