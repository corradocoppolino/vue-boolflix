<template>
  
    <section class="col-sm-6 col-md-4 col-lg-3 col-xl-2">

        <div class="box-film">
            
            <div class="flip-card">
                <div class="flip-card-inner">
                    <div class="flip-card-front">
                        <img v-if="esisteCopertina(copertina)" class="img-fluid" :src="controlloImmagine(copertina)" alt="">
                        <img v-if="esisteCopertina(copertina) === false" class="img-fluid" src="../assets/img/ciao.png" alt="">
                    </div>
                    <div class="flip-card-back">
                        <h6>{{titolo}}</h6>
                        <h6>{{original}}</h6>
                        <flag :iso="controlloLingua(lingua)" />
                        <div>
                            <i :key="index" v-for="(element,index) in Math.ceil(voto/2)" class="fas fa-star"></i>
                            <i :key="index+5" v-for="(element,index) in Math.floor(5 - voto/2)" class="far fa-star"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>

    </section>

</template>

<script>
export default {

    name:"CardsSeries",

    props: {
        titolo: String,
        original: String,
        lingua: String,
        voto: Number,
        copertina: String
    },

    methods: {

        controlloLingua(str){
            if(str === "en"){
                str = "us"
            }else if(str === "ja"){
                str = "jp"
            }
            return str
        },

        controlloImmagine(str){
            let url = 'https://image.tmdb.org/t/p/w200';
            console.log(str);
            return url + str
        },

        esisteCopertina(str){
            if(str != null){
                return true
            }
            return false;
        }

    }

}
</script>

<style lang="scss" scoped>

.box-film{
    margin-top: 40px;
    min-height: 300px;
}

.flip-card {
  background-color: grey;
  perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */

/* Style the back side */
.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
}

//media query

@media screen and (max-width: 764px) {
  .box-film{
      min-height: 305px;
  }
}

@media screen and (max-width: 560px) {
  .box-film{
      min-height: 500px;
  }
}

@media screen and (min-width: 1200px) {
  .box-film{
      min-height: 220px;
  }
}

@media screen and (min-width: 1400px) {
  .box-film{
      min-height: 275px;
  }
}



</style>