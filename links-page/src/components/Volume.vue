<template>
  <button class="muteButton" @click="playAudio" v-if="!audioPlaying">
    <i class="fa-solid fa-volume-xmark"></i>
  </button>
  <button class="muteButton" @click="stopAudio" v-if="audioPlaying">
    <i class="fa-solid fa-volume-high"></i>
  </button>
  <div class="audioElementContainer">
    <div class="audioElement">
      <audio id="audioPlayer" preload="auto">
        <source src="/sounds/buildingOnToWater2.mp3">
      </audio>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      audioPlaying: false
    }
  },
  methods: {
    playAudio() {
      let audioPlayer = document.getElementById('audioPlayer');
      if (audioPlayer.paused) {
        audioPlayer.play();
        this.audioPlaying = true;
      }
    },
    stopAudio() {
      let audioPlayer = document.getElementById('audioPlayer');
      audioPlayer.pause();
      this.audioPlaying = false;
    }
  }
}
</script>

<style scoped>

.muteButton {
}
</style>
