<template>
  <Header />
  <main>
    <div class="goals">
      <p id="title">Choose your top goals</p>
      <p id="subtitle">
        Persub is here to help you improve your financial health. Select your
        top goals from the list to the right and then hit Continue.
      </p>
    </div>
    <div class="grid">
      <div v-for="(detail, index) in details" :key="index">
        <Billing :detail="detail" :index="index" />
      </div>
    </div>
    <button class="submit">submit</button>
  </main>
</template>

<script>
import Header from "./components/Header.vue";
import Billing from "./components/Billing.vue";

export default {
  name: "App",
  components: { Header, Billing },
  data() {
    return {
      details: [
        "Cancel Subscriptions",
        "Lower my Bills",
        "Pay my Bills on Time",
        "Track my Spending",
        "Create a Budget",
        "Grow my Savings",
      ],
    };
  },
};
</script>

<style lang="scss">
@import "./assets/sass/vars";
@import "./assets/sass/mixins";

:root {
  font-size: $font-size;
}

html,
body {
  @include reset;
}

body {
  font: {
    family: $font-family;
    size: 1.4rem;
    weight: 400;
  }
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  background: #f8f8f8;
}

main {
  display: grid;
  grid-template-columns: auto;
  grid-auto-rows: auto;
  grid-template-areas:
    "goals"
    "grid"
    "submit";
  grid-gap: 0.5rem;
  // & > div {
  //   border: 1px solid salmon;
  // }
}

.goals {
  grid-area: goals;
  justify-self: center;
  width: 135rem;
  height: 15rem;
  & p {
    margin: 0;
  }
  & #title {
    font-size: 3rem;
    font-weight: 500;
    margin: 5rem 0 1rem 0;
  }
  & #subtitle {
    width: 45rem;
  }
}

.grid {
  grid-area: grid;
  justify-self: center;
  width: 100rem;
  height: 60rem;
  display: grid;
  grid-template-columns: auto auto auto;
  grid-auto-rows: auto;
  justify-content: center;
  align-content: center;
  grid-column-gap: 2.5rem;
  grid-row-gap: 4.3rem;
  & div {
    animation: load 0.5s forwards;
  }
}

@keyframes load {
  from {
    opacity: 0;
    transform: translateY(-5px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.submit {
  grid-area: submit;
  justify-self: center;
  background: black;
  color: white;
  border: 1px solid black;
  border-radius: 5rem;
  text-transform: uppercase;
  padding: 1.2rem 4rem;
  margin-top: 1rem;
  margin-bottom: 4rem;
  transition: $transition-time ease-out;
  &:hover {
    cursor: pointer;
    background: white;
    color: black;
  }
}

// MEDIA
@media (max-width: 1400px) {
  .goals,
  .grid {
    width: 100rem; // 95rem;
    // border: 1px solid royalblue;
  }
}

@media (max-width: 1100px) {
  .goals,
  .grid {
    width: 70rem;
    // border: 1px solid royalblue;
  }

  .grid {
    grid-template-columns: auto auto;
    grid-gap: 2rem;
    height: auto;
    padding: 2rem 0;
  }
}

@media (max-width: 750px) {
  .goals,
  .grid {
    width: 32rem; // 26rem;
    // border: 1px solid royalblue;
  }

  .goals {
    height: auto;
    & p {
      margin: 0;
    }
    & #title {
      font-size: 2.5rem;
      font-weight: 500;
      margin: 3rem 0 1rem 0;
    }
    & #subtitle {
      width: auto;
      margin-bottom: 1rem;
      text-align: justify;
    }
  }

  .grid {
    grid-template-columns: auto;
    grid-gap: 2rem;
    height: auto;
    // padding: 2rem 0;
  }
}
</style>