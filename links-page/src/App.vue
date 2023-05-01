<script setup>
  import ThreeJS from './components/ThreeJS.vue'
</script>

<template>
  <div class="parentContainer">
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
</script>
