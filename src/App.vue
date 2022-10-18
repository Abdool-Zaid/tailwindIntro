<script setup>
document.addEventListener('contextmenu', function(e) {
  e.preventDefault();
});
let startTime;
let spanWidth = window.innerWidth;
let spanHeight = window.innerHeight;
let xCoor = Math.round(spanWidth * Math.random()) + "px";
let yCoor = Math.round(spanHeight * Math.random()) + "px";
function generateRandomColor() {
  let letters = "0123456789ABCDEF";
  let color = "#";
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color
  }
function moveTarget() {
  document.querySelector("#target").style = `
  display: block;
  color: ${generateRandomColor()};
  top: ${yCoor};
  left: ${xCoor};
    `;
    document.querySelector('body').style=`
    background-color: ${generateRandomColor()};
    `
}
function runTrial() {
  if (startTime == null) {
    startTime = Date.now();
    moveTarget();
    
    document.querySelector('button').style=`display: none;`
  } else if (startTime > 0) {
    xCoor = Math.round(spanWidth * Math.random()) + "px";
    yCoor = Math.round(spanHeight * Math.random()) + "px";
    moveTarget();
    document.querySelector('h1').innerHTML=`
    ${
      (Date.now()-startTime)/1000
    } seconds
    `
    startTime = Date.now();
  }
}
</script>

<template>
  <h1 class="prevent-select">Reaction timer</h1>
  <button class="prevent-select" @click="runTrial()">begin trial</button>
  <p></p>
  <div id="target" @click="runTrial()" class="prevent-select"><p>._.</p></div>
</template>

<style scoped>
.prevent-select {
  -webkit-user-select: none; /* Safari */
  -ms-user-select: none; /* IE 10 and IE 11 */
  user-select: none; /* Standard syntax */
}

#target {
  display:none;
  z-index: 10;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
