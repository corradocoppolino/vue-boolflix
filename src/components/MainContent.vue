<template>
  
    <main class="row">

        <h1 v-if="arrayFilm.length > 0">FILM</h1>

        <cards-film 
        v-for="element in arrayFilm"
        :key="element.id"
        :titolo= element.title
        :original= element.original_title
        :lingua= element.original_language
        :voto= element.vote_average
        />

        <h1 v-if="arraySeries.length > 0">SERIE TV</h1>

        <cards-series 
        v-for="element in arraySeries"
        :key="element.id"
        :titolo= element.name
        :original= element.original_name
        :lingua= element.original_language
        :voto= element.vote_average
        />

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
        background-color: grey;
        width: 100%;
        h1{
            margin-top: 20px;
        }
    }

</style>