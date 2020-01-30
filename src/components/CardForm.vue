/* eslint-disable vue/no-parsing-error */
<template>
  <div class="card-form">
    <div class="card-input">
      <label for="card-number">Card Number</label>
      <input
        type="text"
        id="card-number"
        v-model="cardNumber"
        @change="numberChange"
      />
    </div>
    <div class="card-input">
      <label for="card-holders">Card Holders</label>
      <input type="text" id="card-holders" />
    </div>
    <div class="card-form-row">
      <div class="row-col">
        <div class="ed-group">
          <label for="card-month">Expiration Date</label>
          <select name="card-month" id="card-month">
            <option value selected disabled>Month</option>
            <option v-bind:value="n" v-for="n in 12" v-bind:key="n">{{
              n
            }}</option>
          </select>
          <select name="card-year" id="card-year">
            <option value selected disabled>Year</option>
            <option v-bind:value="n" v-for="(n, i) in 12" v-bind:key="n">{{
              i + minCardYear
            }}</option>
          </select>
        </div>
      </div>
      <div class="row-col">
        <div class="card-input">
          <label for="card-cvv">CVV</label>
          <input type="text" id="card-cvv" />
        </div>
      </div>
    </div>
    <button>Submit</button>
  </div>
</template>

<script>
import bus from "../main";

export default {
  data() {
    return {
      cardName: "",
      cardNumber: "",
      cardMonth: "",
      cardYear: "",
      cardCvv: "",
      m: 10,
      minCardYear: new Date().getFullYear(),
      focusElementStyle: null,
      isInputFocused: false
    };
  },
  methods: {
    numberChange(e) {
      const payload = {
        cardNumber: e.target.value
      };
      // this.cardNumber = e.target.value;
      bus.$emit("numChange", payload);
    }
  }
};
</script>

<style lang="scss" scoped>
.card-form {
  background: #fff;
  z-index: 1;
  position: relative;
  width: 50vw;
  padding: 35px;
  padding-top: 180px;
  border-radius: 10px;
  box-shadow: 0 30px 60px 0 rgba(90, 116, 148, 0.4);
  display: flex;
  flex-direction: column;
  height: auto;
  .card-form-row {
    display: flex;
    flex-direction: row;
    .row-col {
      flex: auto;
      margin-right: 35px;
      &:last-child {
        margin: 0;
        max-width: 150px;
      }
      .ed-group {
        display: flex;
        align-items: flex-start;
        flex-wrap: wrap;
        select {
          flex: 1;
          margin-right: 15px;
          &:last-child {
            margin-right: 0;
          }
        }
      }
    }
  }
  button {
    width: 100%;
    height: 55px;
    background: #2364d2;
    border: none;
    border-radius: 5px;
    font-size: 22px;
    font-weight: 500;
    font-family: "Source Sans Pro", sans-serif;
    box-shadow: 3px 10px 20px 0px rgba(35, 100, 210, 0.3);
    color: #fff;
    margin-top: 20px;
    cursor: pointer;
  }
}
</style>
