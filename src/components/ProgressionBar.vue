<template>
    <div>
        <div class="barra">
            <div class="barra-progresso">

            </div>
            <span>{{progresso}}%</span>
        </div>
    </div>
</template>

<script>
export default {
    props:['progress'],
    data(){
        return{
            progresso:0
        }
    }
}
</script>

<style scoped>
    .barra{
        width: 80vw;
        height: 40px;
        border: 1px solid #ccc;
        border-radius: 10px;
    }
    .barra-progresso{
        width: 0%;
        height: 100%;
        background-color: rgb(15, 187, 24);
        position: relative;
        z-index: -1;
        border-radius: 8px;
    }
    .barra span{
        position: relative;
        top: -30px;
        left: 50%;
        transform: translate(-50%,50%);
    }
</style>