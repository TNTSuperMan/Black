<script setup>
import {ref,onUnmounted} from "vue"
const hours = ref(new Date().getHours())
const minutes = ref(new Date().getMinutes())
const seconds = ref(new Date().getSeconds())
let intid = setInterval(()=>{
    hours.value = new Date().getHours()
    minutes.value = new Date().getMinutes()
    seconds.value = new Date().getSeconds()
},500)
onUnmounted(()=>clearInterval(intid))
</script>
<template>
    <div>
        {{ hours }}:
        {{ minutes }}.
        {{ seconds }}
    </div>
</template>
<style scoped>
div{
    position:fixed;
    left:10%;
    top:10%;
    font-size:50px;
    font-weight: 500;
    color:#555;
    opacity: 0.2;
    padding:30px;
    transition:all 0.4s ease;
}
div:hover{
    opacity:1;
}
</style>