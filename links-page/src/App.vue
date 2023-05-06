<script setup>
  import ThreeJS from './components/ThreeJS.vue'
  import Card from './components/Card.vue'
  import Volume from './components/Volume.vue'
</script>

<template>
  <div class="parentContainer">
    <div class="overlayContainer">
      <div class="muteButtonContainer">
        <Volume></Volume>
      </div>
      <div class="cardsContainer">
        <Card
          :title="'Stream the Music'"
        ></Card>
        <Card
          :title="'Buy the Beats'"
        ></Card>
        <Card
          :title="'Hire Me For Your Next Project'"
        ></Card>
      </div>
    </div>
    <ThreeJS></ThreeJS>
  </div>
</template>

<script>
export default {
  data() {
    return {
    }
  },
  methods: {
  }
}
</script>

<style scoped>

.overlayContainer {
  position: absolute;
  height: 100%;
  width: 100%;
}
.cardsContainer {
  margin: auto;
  width: 100%;
  height: 90vh;
  display: flexbox;
  flex-direction: column;
  gap: 2%;
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
