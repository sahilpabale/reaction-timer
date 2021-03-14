<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click Me <br /></div>
</template>

<script>
export default {
  name: "Block",
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 300px;
  border-radius: 15px;
  background: crimson;
  color: white;
  font-size: 2rem;
  font-weight: 600;
  text-align: center;
  padding: 50px 0;
  margin: 40px auto;
}
</style>
