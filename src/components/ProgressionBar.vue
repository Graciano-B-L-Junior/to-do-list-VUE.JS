<template>
    <div>
        <div class="barra">
            <div class="barra-progresso" :style="{width:progress+'%'}">

            </div>
            <span>{{progress}}%</span>
        </div>
    </div>
</template>

<script>
export default {
    props:['progress'],
    
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
        width: 50%;
        height: 100%;
        background-color: rgb(15, 187, 24);
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