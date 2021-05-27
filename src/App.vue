<template>
  <div id="app">
    
    <header-main @src="searchFilms" />

    <main-content 
    :arrayFilm="films"
    :arraySeries= "series"
    />

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
    apiURLFilm: "https://api.themoviedb.org/3/search/movie",
    apiURLTv: "https://api.themoviedb.org/3/search/tv",
    apiKey: "b6ecad6b36ae1c5ecd7e97efa9a42ecf",
    query: "",
    films: [],
    series: [],
    textFilm: ""
    }
  
  },

  methods: {

    callAxiosFilms(){

      axios.get(this.apiURLFilm,{
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

    callAxiosSeries(){

      axios.get(this.apiURLTv,{
            params:{
                api_key: this.apiKey,
                query: this.query,
                language: "it-IT"
            }
        })
        .then(res => {
            /* console.log(res.data.results); */
            this.series = res.data.results;
            console.log(this.series)
        })

    },

    searchFilms(text){

      this.query= text;
      this.callAxiosFilms();
      this.callAxiosSeries();
    
    }

  },

  beforeCreate() {

    axios.get("https://api.themoviedb.org/3/search/movie?api_key=b6ecad6b36ae1c5ecd7e97efa9a42ecf&query=pokemon&language=it-IT")
      .then(res => {
          /* console.log(res.data.results); */
          this.films = res.data.results;
          console.log(this.films)
      })

    axios.get("https://api.themoviedb.org/3/search/tv?api_key=b6ecad6b36ae1c5ecd7e97efa9a42ecf&query=pokemon&language=it-IT")
      .then(res => {
          /* console.log(res.data.results); */
          this.series = res.data.results;
          console.log(this.series)
      })

  }

}

</script>

<style lang="scss">

  @import '@/assets/style/general';

</style>
