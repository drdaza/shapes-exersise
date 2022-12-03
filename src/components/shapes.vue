<script setup >
import { computed } from '@vue/reactivity';
import { ref } from 'vue';
    //VARIABLES
    let classChanger = ref([0,0,0]);
    //METHODS
    function addView(param) {
        console.log(param);
        if(param == 'square' ){
            classChanger.value[0] += 1;
        }
        if(param== "triangle" ){
            classChanger.value[1] += 1;
        }
        if(param == "circle" ){
            classChanger.value[2] += 1;
        }
        console.log(classChanger.value);
    }
    function restart(){
        classChanger.value = [0,0,0]
    }
    // COMPUTED
    const modifySquare = computed(()=>{
        return {
            'invisible': classChanger.value[0] > 0,
        }
    });
    const modifyTriangle = computed(()=>{
        return{
            'invisible': classChanger.value[1] > 0,
        }
    });
    const modifyCircle = computed(()=>{
        return{
            'invisible': classChanger.value[2] > 0,
        }
    });
    
</script>
<template>
    <div id="container">
        <div :class="['shape','square', modifySquare ]" id="square1" @click="addView('square')">
            <h1></h1>
        </div>
        <div :class="['shape','triangle', modifyTriangle ]" id="triangle2"  @click="addView('triangle')">
            <h1></h1>
        </div>
        <div :class="['shape', 'circle', modifyCircle]" id="circle3"  @click="addView('circle')">
            <h1></h1>
        </div>
    </div>
    <button id="btn-restart" @click="restart()">Restart</button>
</template>
<style lang="scss">
    #container{
        margin: 1vh;
        width: 30%;
        height: 8vh;
        display: flex;
        flex-direction: row;
        justify-content: space-evenly;
        .shape{
            width: 30%;
            background-color: aquamarine;
        }
        .shape:hover{
            transform: translateY(-5px);
        }
        .circle{
            border-radius: 50px;
            background-color: brown;
        }
        .triangle{
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 0 30px 52.0px 30px;
            border-color: transparent transparent #007bff transparent;
            background-color: transparent;

        }
        .square{
            background-color: chocolate;
        }
        .circle:hover{
            border-radius: 50px;
            background-color: rgb(65, 1, 1);
        }
        .triangle:hover{
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 0 30px 52.0px 30px;
            border-color: transparent transparent #a6ff00 transparent;
            background-color: transparent;

        }
        .square:hover{
            background-color: rgb(69, 30, 210);
        }
    }
    .invisible{
        visibility: hidden;
    }
</style>