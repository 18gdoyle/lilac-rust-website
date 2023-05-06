<template>
  <div class="cardContainer">
    <a href="https://li.sten.to/lilac_rust" class="htmlOverlay">
      <h1>{{ title }}</h1>
    </a>
  </div>
</template>

<script>
export default {
  props: {
    title: String,

  }
}
</script>

<style scoped>
.cardContainer {
  width: 80vw;
  height: 15vh;
  margin: auto;
  background-color: rgba(255, 255, 255, .15);  
  backdrop-filter: blur(5px);
}
.htmlOverlay {
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 80%;
  color: white;
}
</style>
