<script setup>
let startTime
let spanWidth=
window.innerWidth
let spanHeight=
window.innerHeight
let xCoor=
Math.round(spanWidth * Math.random())
let yCoor=
Math.round(spanHeight * Math.random())
function runTrial(){
  if (startTime==null){
    startTime= Date.now()
    document.querySelector('#target').style

    
  }
}
</script>

<template>
  <h1>Reaction timer</h1>
  <h4></h4>
  <button @click="runTrial()">begin trial</button>
  <p></p>
  <div id="target" @click="runTrial()"><p>._.</p></div>
</template>

<style scoped>

</style>
