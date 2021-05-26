<template>
  
    <section class="col-md-2">

        <div class="box-film text-center">
            <h6>{{titolo}}</h6>
            <h6>{{original}}</h6>
            <h6>{{lingua}}</h6>
            <h6>{{voto}}</h6>
        </div>

    </section>

</template>

<script>
export default {

    name:"CardsFilm",

    props: {
        titolo: String,
        original: String,
        lingua: String,
        voto: String
    }

}
</script>

<style lang="scss" scoped>

.box-film{
    margin-top: 20px;
    height: 200px;
    background-color: hotpink;
}

</style>