<template>
  <div class="footer-bar-game">
    <div class="navs">
      <div
        @click.prevent="onClick(nav)"
        class="nav"
        v-for="(nav, index) in navs"
        :key="index"
        :class="{ active: currentComponent === nav.component }"
      >
        <i :class="nav.icon"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FooterBarGame",

  props: ["currentComponent"],

  data() {
    return {
      navs: [
        {
          name: "Map",
          icon: "fas fa-map",
          component: "MapGame",
        },
        {
          name: "Game",
          icon: "fas fa-clone",
          component: "CardsGame",
        },
        {
          name: "Members",
          icon: "fas fa-users",
          component: "MembersGame",
        },
      ],
    };
  },

  methods: {
    onClick(nav) {
      this.$emit("change", nav);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/variables.scss";

.footer-bar-game {
  background-color: $primary;
  color: $white;
  padding: 15px 20px;
  grid-gap: 15px;
  margin-top: auto;

  .navs {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;

    .nav {
      font-size: 18px;
      display: flex;
      justify-content: center;
      align-items: center;
      transition: all 0.3s;
      min-width: 30px;
      min-height: 30px;
      -webkit-tap-highlight-color: rgba(0, 0, 0, 0);

      &.active {
        transform: scale(1.3);
        color: #01142f;
      }
    }
  }
}
</style>
