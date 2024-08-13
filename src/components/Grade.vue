<script setup>
import {ref,onUnmounted,computed} from "vue"
const x = ref(0)
const y = ref(0)
let tick = Math.random()*100
let rand1  = Math.random() * 100
let rand2  = Math.random() * 100
let rand3  = 10 + Math.random() * 30
let rand4  = 10 + Math.random() * 30
const style = computed(()=>{
    let style = "left:"
    style += x.value
    style += "px;top:"
    style += y.value;
    style += "px"
    return style
})
let intid = setInterval(()=>{
    tick+=0.01
    x.value = (Math.sin(tick/rand3+rand1)+1) * (window.innerWidth/2-100)
    y.value = (Math.sin(tick/rand4+rand2)+1) * (window.innerHeight/2-100)
},1)
onUnmounted(()=>clearInterval(intid))
</script>
<template>
    <div :style="style"></div>
</template>
<style scoped>
div{
    background:radial-gradient(rgba(255,255,255,0.07),rgba(0,0,0,0) 70%,rgba(0,0,0,0) 100%);
    width: 250px;
    height:250px;
    position:fixed;
    z-index: -2;
}
</style>