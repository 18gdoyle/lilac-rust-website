<script setup>
  import ThreeJS from './components/ThreeJS.vue'
  import Card from './components/Card.vue'
  import Volume from './components/Volume.vue'
  import SoundBetterCard from './components/SoundBetterCard.vue';
  import StreamTheMusicCard from './components/StreamTheMusicCard.vue';
</script>

<template>
  <div class="overlayContainer">
    <div class="muteButtonContainer">
      <Volume></Volume>
    </div>
    <div class="cardsContainer">
      <StreamTheMusicCard
        :title="'Stream the Music'"
        :href="'https://li.sten.to/lilac_rust'"
      ></StreamTheMusicCard>
      <Card
        :title="'Buy the Beats'"
        :href="'https://airbit.com/lilacrust'"
      ></Card>
      <SoundBetterCard
        :title="'Hire Me For a Project'"
      ></SoundBetterCard>
    </div>
    <div class="socialMediaLinksContainer">
      <a class="socialMediaButton" href="https://www.tiktok.com/@lilac_rust">
        <i class="fa-brands fa-tiktok socialMediaIcon"></i>
      </a>
      <a class="socialMediaButton" href="https://www.instagram.com/lilac_rust_music/">
        <i class="fa-brands fa-instagram socialMediaIcon"></i>
      </a>
      <a class="socialMediaButton" href="https://www.youtube.com/@lilacrust8805">
        <i class="fa-brands fa-youtube socialMediaIcon"></i>
      </a>
    </div>
  </div>
  <div>
    <ThreeJS></ThreeJS>
  </div>
</template>

<script>
export default {
    data() {
        return {};
    },
    methods: {},
    components: { SoundBetterCard, StreamTheMusicCard }
}
</script>

<style scoped>
.overlayContainer {
  position: absolute;
  height: 100%;
  width: 100%;
}
.muteButtonContainer {
  position: relative;
  width: 100%;
  height: 10vh;
  display: flex;
  flex-direction: row;
  justify-content: center;
  text-align: center;
}
.cardsContainer {
  width: 100%;
  height: 75vh;
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  text-align: center;
}

.socialMediaLinksContainer {
  display: flex;
  flex-direction: row;
  justify-content: center;
  width: 100%;
}

.socialMediaButton {
  height: 8vh;
  width: 8vh;
  display: flex;
  justify-content: center;
  border-radius: 100vh;
  background-color: rgba(255, 255, 255, .15);  
  backdrop-filter: blur(5px);
  text-align: center;
  margin-left: 2vw;
  margin-right: 2vw;
  color: white;
}

.socialMediaIcon {
  font-size: 5vh;
  margin: auto;
}

@media only screen and (max-width: 600px) {

  .muteButtonContainer {
    position: relative;
    width: 100%;
    height: 10vh;
  }
}
</style>
