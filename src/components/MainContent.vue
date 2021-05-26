<template>
  
    <main class="row">

        <cards-film 
        v-for="element in array"
        :key="element.id"
        :titolo= element.title
        :original= element.original_title
        :lingua= element.original_language
        :voto= element.vote_average
        />

    </main>

</template>

<script>
import CardsFilm from './CardsFilm.vue'

export default {
    components: { 
      CardsFilm 
    },
    
    name: 'MainContent',

    props: {
        array: Array,
    }
    
}
</script>

<style lang='scss' scoped>

    main{
        background-color: grey;
        width: 100%;
    }

</style>