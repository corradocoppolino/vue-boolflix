<template>
  <div id="app">
    
    <header-main @src="searchFilms" />

    <main-content />

  </div>
</template>

<script>

import HeaderMain from './components/HeaderMain.vue'
import MainContent from './components/MainContent.vue'
import axios from 'axios'

export default {

  name: 'App',

  components: {
    HeaderMain,
    MainContent
  },

  data(){

  return{
    apiURL: "https://api.themoviedb.org/3/search/movie",
    apiKey: "b6ecad6b36ae1c5ecd7e97efa9a42ecf",
    query: "matrix",
    films: [],
    textFilm: ""
    }
  
  },

  methods: {

    callAxios(){

      axios.get(this.apiURL,{
            params:{
                api_key: this.apiKey,
                query: this.query,
                language: "it-IT"
            }
        })
        .then(res => {
            /* console.log(res.data.results); */
            this.films = res.data.results;
            console.log(this.films)
        })

    },

    searchFilms(text){

      this.query= text;
      this.callAxios();
    
    }

  },

  beforeCreate() {

    axios.get(this.apiURL,{
      params:{
        api_key: this.apiKey,
        query: this.query,
        language: "it-IT"
        }
    })
      .then(res => {
          /* console.log(res.data.results); */
          this.films = res.data.results;
          console.log(this.films)
      })

  }

}

</script>

<style lang="scss">

  @import '@/assets/style/general';

</style>
