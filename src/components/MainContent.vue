<template>
  
    <main>



    </main>

</template>

<script>

import axios from 'axios';

export default {
    
    name: 'MainContent',

    data(){
        return{
            apiURL: "https://api.themoviedb.org/3/search/movie",
            apiKey: "b6ecad6b36ae1c5ecd7e97efa9a42ecf",
            query: "pokemon",
            films: []
        }
    },

    created(){

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

<style lang='scss' scoped>

    main{
        height: 1000px;
        background-color: grey;
        width: 100%;
    }

</style>