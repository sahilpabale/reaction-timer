<template>
  <div class="score">
    {{ score }} ms <br />
    <div class="rank">{{ rank }}</div>
  </div>
</template>

<script>
export default {
  name: "Results",
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = `Bird's Eye!`;
    } else if (this.score < 400) {
      this.rank = `Rapid Reflexes!`;
    } else {
      this.rank = `Snail pace...`;
    }
  },
};
</script>

<style>
.score {
  width: 300px;
  border-radius: 15px;
  background: rgb(228, 228, 228);
  color: crimson;
  font-size: 2rem;
  font-weight: 600;
  text-align: center;
  padding: 50px 0;
  margin: 40px auto;
}

.rank {
  font-size: 1rem;
  font-weight: 400;
  background: crimson;
  color: white;
  width: fit-content;
  padding: 10px;
  margin: 20px;
  border-radius: 5px;
}
</style>
