<template>
  <div class="cardContainer">
    <div class="card">
      <a :href=href class="cardItemsContainer">
        <i class="fa-brands fa-soundcloud cardIcon"></i>
        <h1 class="cardTitle">{{ title }}</h1>
        <i class="fa-brands fa-soundcloud cardIcon"></i>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    href: String,
  }
}
</script>

<style scoped>
.cardContainer {
  margin: auto;
}

.card {
  width: 80vw;
  height: 15vh;
  border-radius: 20px;
  background-color: rgba(255, 255, 255, .15);
  backdrop-filter: blur(5px);
  text-align: center;
}
.cardTitle {
  margin-left: 2vw;
  margin-right: 2vw;
}
.cardItemsContainer {
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 80%;
  color: white;
}

.cardIcon {
  font-size: 10vh;
}
</style>
