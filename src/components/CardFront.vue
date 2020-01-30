<template>
  <div class="card-front">
    <img
      src="https://raw.githubusercontent.com/muhammederdem/credit-card-form/master/src/assets/images/visa.png"
      alt="vise"
      class="card-logo"
    />
    <img
      src="https://raw.githubusercontent.com/muhammederdem/credit-card-form/master/src/assets/images/chip.png"
      alt="holo"
      class="card-holo"
    />
    <div class="card-bottom">
      <div class="card-number">
        <p class="details-info large-font">{{ cardNumber }}</p>
      </div>
      <div class="card-details">
        <div class="card-holder">
          <p class="trans-text">Card Holder</p>
          <p class="details-info">full name</p>
        </div>
        <div class="expires">
          <p class="trans-text">Expires</p>
          <p class="details-info">MM/YY</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { bus } from "../main";

export default {
  data() {
    return {
      cardNumber: ""
    };
  },

  created() {
    bus.$on("numChange", ({ nimber }) => {
      this.cardNumber = nimber;
    });
  }
};
</script>

<style lang="scss" scoped>
.card-front {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  position: absolute;
  top: 56px;
  left: calc(50vw - 500px / 2);
  padding: 25px;
  height: 279px;
  width: 430px;
  z-index: 2;
  border-radius: 15px;
  text-shadow: 7px 6px 10px rgba(14, 42, 90, 0.8);
  background: url("https://videohive.img.customer.envatousercontent.com/files/4cc45810-7b67-4f07-bb54-a6d92fdc2d9e/inline_image_preview.jpg?auto=compress%2Cformat&fit=crop&crop=top&max-h=8000&max-w=590&s=ea67f83de7eaf3d4e81e33bf8ef00ee1");

  .card-logo {
    transform: scale(0.5);
    position: absolute;
    top: 0;
    right: -26px;
  }
  .card-holo {
    transform: scale(0.6);
    position: absolute;
    top: 8px;
    left: 6px;
  }
  .card-bottom {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 50%;
    padding: 0 25px 25px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    .card-details {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      width: 100%;
    }
    .details-info {
      color: #fff;
      text-transform: capitalize;
      font-size: 18px;
      text-shadow: 7px 6px 10px rgba(14, 42, 90, 0.8);
    }
    .trans-text {
      color: #fff;
      opacity: 0.7;
      font-size: 13px;
      padding-bottom: 6px;
    }
    .large-font {
      font-size: 27px;
      font-weight: 500;
    }
  }
}
</style>
