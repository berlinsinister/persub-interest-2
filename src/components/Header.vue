<template>
  <div class="header">
    <div class="header-content">
      <div class="logo"><b>Per</b>sub</div>
      <nav v-if="windowWidth > 750">
        <div id="interests" class="passive-link">Interests</div>
        <div id="goals" class="active-link">Goals</div>
        <div id="feed" class="passive-link">Feed</div>
      </nav>
      <nav v-else>
        <div id="interests" class="passive-link" title="Interests">
          <i class="fas fa-heart"></i>
        </div>
        <div id="goals" class="active-link" title="Goals">
          <i class="fas fa-bullseye"></i>
        </div>
        <div id="feed" class="passive-link" title="Feed">
          <i class="fas fa-rss"></i>
        </div>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      windowWidth: window.innerWidth,
    };
  },
  mounted() {
    this.$nextTick(() => {
      window.addEventListener("resize", this.onResize);
    });
  },
  beforeUnmount() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.windowWidth = window.innerWidth;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/sass/vars";
@import "../assets/sass/mixins";

.active-link {
  color: $gray;
}

.passive-link {
  color: #a1a1a1;
}

.header {
  width: 100%;
  height: 10rem;
  @include flex-centered-totally;
  background: white;
  box-shadow: 0 5px 10px -6px rgba(black, 0.1);
}

.header-content {
  width: 155rem;
  @include flex-space-between;
  // border: 1px solid blue;
}

.logo {
  font-size: 4rem;
  color: $gray;
}

nav {
  display: flex;
  font-size: 1.8rem;
  font-weight: 500;
  // border: 1px solid lawngreen;
  & div {
    border-bottom: 3px solid transparent;
    margin-top: 3.7rem;
    padding: 0 1rem 3.7rem 1rem;
    transition: $transition-time ease-out;
    &:hover {
      cursor: pointer;
      border-bottom: 3px solid $gray;
    }
  }
  & #interests,
  & #goals {
    margin-right: 10rem;
  }
  & #feed {
    margin-right: 58rem;
  }
}

// MEDIA
@media (max-width: 1600px) {
  .header-content {
    width: 135rem;
  }

  nav {
    & #feed {
      margin-right: 0; // 40rem;
    }
  }
}

@media (max-width: 1400px) {
  .header-content {
    width: 100rem; // 95rem;
  }
}

@media (max-width: 1100px) {
  .header-content {
    width: 70rem;
  }

  nav {
    & #interests,
    & #goals {
      margin-right: 5rem;
    }
  }
}

@media (max-width: 750px) {
  .header-content {
    width: 32rem; // 26rem;
    // border: 1px solid blue;
  }

  nav {
    & div {
      border: none;
      margin: 0;
      padding: 0;
      font-size: 2.5rem;
      &:hover {
        border-bottom: none;
        color: $gray;
      }
    }
    & #interests,
    & #goals {
      margin-right: 1.5rem;
    }
  }
}
</style>