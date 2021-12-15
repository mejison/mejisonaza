<template>
  <div class="welcome w-100 h-100">
    <div class="logo">
      <img src="@/assets/card-games.png" alt="logo" />
    </div>
    <btn class="start-game" @click="onClickCreateGame">Create Game</btn>
  </div>
</template>

<script>
import { Btn } from "@/components";

export default {
  components: {
    Btn,
  },

  methods: {
    onClickCreateGame() {},
  },
};
</script>

<style lang="scss">
.welcome {
  background: linear-gradient(to bottom, #c5f0f8, #ffded5);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding: 50px;

  .logo {
    max-width: 200px;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }

  .start-game {
    max-width: 200px;
  }
}
</style>
