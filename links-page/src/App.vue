<script setup>
  import ThreeJS from './components/ThreeJS.vue'
  import Card from './components/Card.vue'
</script>

<template>
  <div class="parentContainer">
    <div class="cardContainer">
      <div class="htmlOverlay">
        Stream the Music
      </div>
    </div>
    
    <ThreeJS></ThreeJS>
    <div class="audioElementContainer">
      <div class="audioElement">
        <audio id="audioPlayer" preload="auto">
          <source src="/sounds/buildingOnToWater2.mp3">
        </audio>
      </div>
    </div>
  </div>
</template>

<style scoped>

.cardContainer {
  position: absolute;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-left: 30vw;
  width: 40vw;
  height: 90vh;
}
.htmlOverlay {
  width: 100%;
  height: 15%;
  box-shadow: 0 0 1rem 0 rgba(0, 0, 0, .2); 
  border-radius: 5px;
  position: absolute;
  z-index: 1;
  background: inherit;
  overflow: hidden;
  text-align: center;
}

.htmlOverlay:before {
  content: "";
  position: absolute;
  background: inherit;
  z-index: -1;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  box-shadow: inset 0 0 2000px rgba(255, 255, 255, .5);
  filter: blur(10px);
  margin: -20px;
}

@media only screen and (max-width: 600px) {
  .cardContainer {
    margin-left: 10vw;
    width: 80vw;
  }
}
  .parentContainer {
    position: relative;
  }
  .audioElementContainer {
    position: absolute;
    display: flex;
    align-items: center;
    margin: auto;
    top: 2vw;
    width: 100%;
  }
</style>

<script>
/*
  window.addEventListener('touchstart', () => {
    let audioPlayer = document.getElementById('audioPlayer');
    if (audioPlayer.paused) {
      audioPlayer.play();
    }
  })
  window.addEventListener('click', () => {
    let audioPlayer = document.getElementById('audioPlayer');
    if (audioPlayer.paused) {
      audioPlayer.play();
    }
  })
*/
</script>
