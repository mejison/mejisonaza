<template>
  <div class="game w-100 h-100">
    <nav-bar-game :url="url" />
    <div class="content">
      <component :is="currentComponentId"></component>
    </div>
    <footer-bar-game
      :current-component="currentComponentId"
      @change="onChangeNav"
    />
  </div>
</template>

<script>
import {
  NavBarGame,
  FooterBarGame,
  MapGame,
  MembersGame,
  CardsGame,
} from "@/components";

export default {
  components: {
    NavBarGame,
    FooterBarGame,
    MapGame,
    MembersGame,
    CardsGame,
  },

  data() {
    return {
      url: `${location.protocol}//${location.host}/game/2f2f2f2f2f`,
      currentComponentId: "MapGame",
    };
  },

  methods: {
    onChangeNav(nav) {
      this.currentComponentId = nav.component;
    },
  },
};
</script>

<style lang="scss">
.game {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
</style>
