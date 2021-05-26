<template>
  
    <header>
        
        <div class="container d-flex justify-content-between align-items-center">

            <h1>BOOLFIX</h1>

            <div class="search d-flex">
                <input v-model="cerca" class="form-control" type="text" placeholder="Cerca un film...">
                <button type="button" class="btn btn-danger">Primary</button>
            </div>

        </div>

    </header>

</template>

<script>
export default {
    
    name: 'HeaderMain',

    data(){
        return{
            cerca: "",
        }
    }

}
</script>

<style lang='scss' scoped>

    header{
        height: 100px;
        background-color: black;
        width: 100%;
        .container{
            height: 100%;
            h1{
                color: red;
            }
        }
    }

</style>