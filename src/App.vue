<template>
  <div id="app">
    
    <header-main />

    <main-content />

  </div>
</template>

<script>

import HeaderMain from './components/HeaderMain.vue'
import MainContent from './components/MainContent.vue'

export default {

  name: 'App',

  components: {
    HeaderMain,
    MainContent
  }

}

</script>

<style lang="scss">

  @import '@/assets/style/general';

</style>
