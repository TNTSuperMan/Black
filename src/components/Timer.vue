<script setup>
import {ref,onUnmounted} from "vue"
const minutes = ref(0)
const seconds = ref(0)
let time = 0
const intid = ref(0)
function Sync(){
    minutes.value = Math.floor(time / 60)
    seconds.value = time % 60
}
function Start(){
    intid.value = setInterval(()=>{
        time++
        Sync()
    },1000)
}
function Stop(){
    if(intid.value){
        clearInterval(intid.value)
        intid.value = 0
    }
}
function Reset(){
    Stop()
    time = 0
    Sync()
}
onUnmounted(Stop)
</script>
<template>
    <div>
        {{ minutes }}:
        {{ seconds }}
        <button @click="intid ? Stop() : Start()">{{ intid ? 'Stop' : 'Start' }}</button>
        <button @click="Reset">Reset</button>
    </div>
</template>
<style scoped>
div{
    position:fixed;
    left:10%;
    bottom:10%;
    font-size:20px;
    opacity:0.2;
    transition:all 1s ease;
    padding:30px;
    color:#555;
}
div:hover{
    opacity:1;
}
button{
    background:#000;
    color:#555;
    border:1px #555 solid;
    padding:7px;
    border-radius: 10px;
    font-size:15px;
    transition: all 0.4s ease;
    margin:5px;
}
button:hover{
    background:#111;
}
</style>