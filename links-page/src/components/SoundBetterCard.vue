<template>
  <div class="cardContainer">
    <div class="card">
      <a href="https://soundbetter.com/profiles/320009-lilac-rust" title="Lilac Rust profile on SoundBetter" class="cardItemsContainer" >
        <img alt="Lilac Rust, Full instrumental production on SoundBetter" 
          src="https://d2p6ecj15pyavq.cloudfront.net/assets/SoundBetterBadge-c84cb3e75c4267f5bee41f7f617a81d9.svg" 
          class="soundBetterBadge"
        />
        <h1 class="cardTitle">{{ title }}</h1>
        <img alt="Lilac Rust, Full instrumental production on SoundBetter" 
          src="https://d2p6ecj15pyavq.cloudfront.net/assets/SoundBetterBadge-c84cb3e75c4267f5bee41f7f617a81d9.svg" 
          class="soundBetterBadge"
        />
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

.cardItemsContainer {
  height: 100%;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 80%;
  color: white;
}

.cardTitle {
  margin-left: 2vw;
  margin-right: 2vw;
}

.card {
  width: 80vw;
  height: 15vh;
  position: relative;
  border-radius: 20px;
  background-color: rgba(255, 255, 255, .15);
  backdrop-filter: blur(5px);
  text-align: center;
}
.soundBetterBadge {
  height: 10vh;
}
</style>
