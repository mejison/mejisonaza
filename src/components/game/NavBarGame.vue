<template>
  <div class="nav-bar-game">
    <div class="url">
      <input
        type="text"
        class="input-field"
        :value="url"
        placeholder="Game URL"
      />
    </div>
    <div class="qr">
      <img :src="qrCodeSrc || '//placehold.it/32x32'" alt="Game URL" />
    </div>
  </div>
</template>

<script>
import QRCode from "qrcode";

export default {
  name: "NavBarGame",

  props: ["url"],

  data() {
    return {
      qrCodeSrc: "",
    };
  },

  mounted() {
    this.generateQRcode();
  },

  methods: {
    generateQRcode() {
      const canvas = document.createElement("canvas");
      QRCode.toCanvas(canvas, this.url, (error) => {
        if (error) console.error(error);
        this.qrCodeSrc = canvas.toDataURL();
      });
    },
  },

  watch: {
    url() {
      this.generateQRcode();
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/variables.scss";

.nav-bar-game {
  background-color: $primary;
  color: $white;
  padding: 15px 20px;
  display: grid;
  grid-template-columns: 1fr 30px;
  grid-gap: 15px;
  margin-bottom: auto;

  .input-field {
    background: $white;
    border: none;
    outline: none;
    border-radius: 25px;
    padding: 10px 15px;
    width: 100%;
  }

  .qr {
    width: 32px;
    height: 32px;

    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}
</style>
