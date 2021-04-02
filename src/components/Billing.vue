<template>
  <div
    class="billing-container"
    :style="index === 1 || index === 5 ? orange : standard"
  >
    <div id="detail">{{ detail }}</div>
  </div>
</template>

<script>
export default {
  name: "Billing",
  props: {
    detail: String,
    index: Number,
  },
  data() {
    return {
      orange: {
        background: "#ee7038",
        color: "white",
      },
      standard: {
        background: "white",
        color: "#5c5c5c",
      },
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.billing-container {
  width: 26rem;
  height: 20rem;
  border-radius: 1rem;
  box-shadow: 0 0 10px rgba(black, 0.05);
  transition: $transition-time ease-out;
  position: relative;
  &:hover {
    cursor: pointer;
    border-radius: 3rem;
    box-shadow: 0 0 10px rgba(black, 0.1);
  }
  & #detail {
    font-size: 2.2rem;
    width: 12rem;
    position: absolute;
    bottom: 3rem;
    left: 2.5rem;
    // border: 1px solid black;
  }
}
</style>