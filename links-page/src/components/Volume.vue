<template>
  <button class="muteButton" @click="playAudio" v-if="!audioPlaying">
    <i class="fa-solid fa-volume-xmark volumeIcon"></i>
    <h2 class="buttonText">
      Start Vibe
    </h2>
    <i class="fa-solid fa-volume-xmark volumeIcon"></i> 
  </button>
  <button class="muteButton" @click="stopAudio" v-if="audioPlaying">
    <i class="fa-solid fa-volume-high volumeIcon"></i>
    <h2 class="buttonText">
      End Vibe
    </h2>
    <i class="fa-solid fa-volume-high volumeIcon"></i> 
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
.buttonText {
  text-align: center;
}
.volumeIcon {
  font-size: 3vh;
  margin: auto;
  display: flex;
  justify-content: center;
}
.muteButton {
  margin: auto;
  margin-top: 1.5%;
  width: 20%;
  height: 80%;
  border-radius: 20px;
  background-color: rgba(255, 255, 255, .15);
  backdrop-filter: blur(5px);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 80%;
  color: white;
}

@media only screen and (max-width: 600px) {
  .muteButton {
    margin-top: 8%;
    width: 70%;
  }
}
</style>
