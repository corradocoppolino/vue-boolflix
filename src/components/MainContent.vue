<template>
  
    <main>

        <div class="container row">

            <h1 class="text-aling-center" v-if="arrayFilm.length > 0">FILM</h1>

            <cards-film 
            v-for="element in arrayFilm"
            :key="element.id"
            :titolo= element.title
            :original= element.original_title
            :lingua= element.original_language
            :voto= element.vote_average
            :copertina= element.poster_path
            />

            <h1 v-if="arraySeries.length > 0">SERIE TV</h1>

            <cards-series 
            v-for="element in arraySeries"
            :key="element.id"
            :titolo= element.name
            :original= element.original_name
            :lingua= element.original_language
            :voto= element.vote_average
            :copertina= element.poster_path
            />


        </div>

    </main>

</template>

<script>
import CardsFilm from './CardsFilm.vue'
import CardsSeries from './CardsSeries.vue'

export default {
    components: { 
        CardsFilm,
        CardsSeries 
    },
    
    name: 'MainContent',

    props: {
        arrayFilm: Array,
        arraySeries: Array
    }
    
}
</script>

<style lang='scss' scoped>

    main{
        background-color: black;
        height: calc(100vh - 100px);
        overflow: auto;
        padding-bottom: 100px;
        width: 100%;
        .container{
            width: 90%;
            margin: auto;
        }
        h1{
            margin-top: 30px;
            color: white;
        }
    }

</style>