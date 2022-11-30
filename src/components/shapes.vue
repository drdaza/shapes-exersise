<script setup >
import { ref } from 'vue';

    let classChanger = ref("shape");
    let square = ref("square");
    let triangle = ref("triangle");
    let circle = ref("circle");

    function addView() {
        if(square.value == "square" && classChanger.value == "shape"){
            classChanger.value += " invisible";
        }
    }
</script>
<template>
    <div id="container">
        <div :class="classChanger" :id="square" @click="addView()">
            <h1></h1>
        </div>
        <div :class="classChanger" :id="triangle"  @click="addView()">
            <h1></h1>
        </div>
        <div :class="classChanger" :id="circle"  @click="addView()">
            <h1></h1>
        </div>
    </div>
    <button id="btn-restart">Restart</button>
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
        #circle{
            border-radius: 50px;
            background-color: brown;
        }
        #triangle{
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 0 30px 52.0px 30px;
            border-color: transparent transparent #007bff transparent;
            background-color: transparent;

        }
        #square{
            background-color: chocolate;
        }
        #circle:hover{
            border-radius: 50px;
            background-color: rgb(65, 1, 1);
        }
        #triangle:hover{
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 0 30px 52.0px 30px;
            border-color: transparent transparent #a6ff00 transparent;
            background-color: transparent;

        }
        #square:hover{
            background-color: rgb(69, 30, 210);
        }
    }
</style>