<template>
  <form action="" @submit.prevent @reset.prevent method="" class="form">
    <div class="form__wrapper">
      <div class="form__container">
        <label class="form__left-side" for="designation">Designation</label>
        <div class="form__right-side">
          <select name="" id="designation">
            <option selected value="Match Checkout Setting">
              Match Checkout Setting
            </option>
          </select>
        </div>
      </div>
      <div class="form__container">
        <label class="form__left-side" for="goal">Goal </label>
        <div class="form__right-side form__right-side_nowrap">
          <input type="text" value="$10.00" id="goal" />
          <select name="currency" id="currency">
            <option value="USD">USD</option>
            <option value="EUR">EUR</option>
            <option value="RUB">RUB</option>
          </select>
        </div>
      </div>
      <div class="form__container">
        <label class="form__left-side form__left-side_lh-decrease"
          >Default Amount</label
        >
        <div class="form__right-side">
          <div class="form__radio-container">
            <input type="radio" id="radio1" name="defAmount" />
            <label class="form__radio-label" for="radio1"
              >Match Checkout Setting</label
            >
          </div>
          <div class="form__radio-container">
            <input type="radio" id="radio2" checked name="defAmount" />
            <label class="form__radio-label" for="radio2">Customize</label>
          </div>
        </div>
      </div>
      <div class="form__container">
        <span class="form__left-side"></span>
        <div class="form__right-side">
          <div class="form__checkbox-container">
            <input type="checkbox" id="checkbox1" />
            <label class="form__checkbox-label" for="checkbox1"
              >Allow donor to change default currency</label
            >
          </div>
        </div>
      </div>
      <div class="form__container form__container_range">
        <label
          for="size-range"
          class="form__left-side form__left-side_lh-decrease"
          >Border size</label
        >
        <div class="form__right-side form__right-side_range">
          <input
            v-model="borderSizeValue"
            min="0"
            max="3"
            step="1"
            type="range"
            id="size-range"
          />
          <span>{{ borderSizeValue }}px</span>
        </div>
      </div>
      <div class="form__container form__container_range">
        <label
          for="radius-range"
          class="form__left-side form__left-side_lh-decrease"
          >Border radius</label
        >
        <div class="form__right-side form__right-side_range">
          <input
            v-model="borderRadiusValue"
            min="0"
            max="20"
            step="1"
            type="range"
            id="radius-range"
          />
          <span>{{ borderRadiusValue }}px</span>
        </div>
      </div>
    </div>
    <div class="form__buttons-container">
      <button type="submit" class="btn btn_submit">Save changes</button>
      <button type="reset" class="btn btn_cancel">Cancel</button>
    </div>
  </form>
</template>
<script>
export default {
  data() {
    return {
      borderSizeValue: 0,
      borderRadiusValue: 0,
    };
  },
  mounted() {
    let inputs = document.querySelectorAll("input[type=range]");
    inputs.forEach((item) => {
      item.oninput = () => {
        let value = (item.value - item.min) / (item.max - item.min);
        console.log(value);
        item.style.backgroundImage = [
          "-webkit-gradient(",
          "linear, ",
          "left top, ",
          "right top, ",
          "color-stop(" + value + ", #00a651), ",
          "color-stop(" + value + ", #dbdcde)",
          ")",
        ].join("");
      };
    });
  },
};
</script>
<style lang="scss">
.form {
  &__buttons-container {
    display: flex;
    border-top: 1px solid $border-grey;
    box-sizing: border-box;
    border-radius: 0px 0px 8px 8px;
    background: $sand;
    padding: 24px 0 24px 32px;
  }
  &__wrapper {
    padding: 40px 0 40px 60px;
  }
  &__container {
    display: flex;
    align-items: flex-start;
    &:not(:last-child) {
      margin-bottom: 24px;
    }
    &_range {
      align-items: center;
    }
  }
  &__left-side {
    display: flex;
    flex-basis: 125px;
    justify-content: flex-end;
    margin-right: 16px;
    line-height: 40px;
    user-select: none;
    &_lh-decrease {
      line-height: 24px;
    }
  }
  &__right-side {
    flex-basis: 296px;
    display: flex;
    position: relative;
    justify-content: space-between;
    flex-wrap: wrap;
    align-items: center;
    &_range {
      justify-content: flex-start;
      display: flex;
      align-items: center;
      span {
        margin-left: 16px;
      }
    }
    &_nowrap {
      flex-wrap: nowrap;
    }
  }
  input[type="text"],
  select {
    height: 40px;
    border: 1px solid #a9abae;
    box-sizing: border-box;
    border-radius: 6px;
    background-color: #fff;
    text-indent: 12px;
    outline: none;
    transition: 0.3s;
    font-size: 16px;
    line-height: 24px;
    &:focus {
      border-color: $green;
    }
  }
  select {
    -moz-appearance: none; /* Firefox */
    -webkit-appearance: none; /* Safari and Chrome */
    appearance: none;
    position: relative;
    background: url(../assets/img/arrow.svg) no-repeat calc(100% - 10px) 50%;
  }
  &__radio-container {
    display: flex;
    flex-basis: 100%;
    align-items: center;
    &:not(:last-child) {
      margin-bottom: 16px;
    }
    input[type="radio"] {
      opacity: 0;
      position: relative;
      z-index: -1;
      width: 0;
      height: 0;

      &:checked {
        + .form__radio-label::before {
          border: 2px solid $green;
        }
        + .form__radio-label::after {
          opacity: 1;
        }
      }
    }
  }
  &__radio-label {
    user-select: none;
    position: relative;
    cursor: pointer;
    display: flex;
    align-items: center;
    &::before {
      display: inline-block;
      content: "";
      position: relative;
      width: 24px;
      height: 24px;
      border: 1px solid #a9abae;
      box-sizing: border-box;
      border-radius: 50%;
      margin-right: 12px;
      transition: 0.1s;
    }
    &::after {
      content: "";
      width: 12px;
      height: 12px;
      background-color: $green;
      border-radius: 50%;
      position: absolute;
      left: 6px;
      opacity: 0;
      transition: 0.3s;
    }
  }
  &__checkbox-container {
    input[type="checkbox"] {
      opacity: 0;
      position: absolute;
      z-index: -1;
      width: 0;
      height: 0;
      &:checked {
        + .form__checkbox-label::before {
          border: 2px solid $green;
        }
        + .form__checkbox-label::after {
          opacity: 1;
        }
      }
    }
  }
  &__checkbox-label {
    user-select: none;
    position: relative;
    display: flex;
    align-items: center;
    &::before {
      content: "";
      border: 1px solid #a9abae;
      position: relative;
      flex-basis: 24px;
      flex-shrink: 0;
      height: 24px;
      display: inline-block;
      margin-right: 12px;
      border-radius: 4px;
      // transition: 0.1s;
      box-sizing: border-box;
    }
    &::after {
      content: url(../assets/img/check.svg);
      opacity: 0;
      position: absolute;
      left: 4.5px;
      transition: 0.1s;
    }
  }
  input[type="range"] {
    -webkit-appearance: none;
    -moz-apperance: none;
    width: 218px;
    height: 3px;
    background: $border-grey;
    outline: none;
    background-image: -webkit-gradient(
      linear,
      left top,
      right top,
      color-stop(0, $green),
      color-stop(0, $border-grey)
    );
    &::-webkit-slider-thumb {
      -webkit-appearance: none;
      -moz-apperance: none;
      width: 19px;
      height: 19px;
      -webkit-border-radius: 50%;
      -moz-border-radius: 50%;
      -ms-border-radius: 50%;
      -o-border-radius: 50%;
      border-radius: 50%;
      background-color: $green;
    }
  }
}
#designation {
  width: 100%;
}
#goal {
  display: flex;
  flex: 1 1 192px;
}
#currency {
  display: flex;
  margin-left: 15px;
  flex: 1 0 80px;
}
.btn {
  font-size: 16px;
  max-height: 48px;
  line-height: 24px;
  border-radius: 6px;
  padding: 12px 24px;
  border: none;
  box-sizing: border-box;
  margin-right: 16px;
  transition: 0.3s;
  &_submit {
    border: 1px solid $green;
    background-color: $green;
    color: #fff;
    &:hover {
      background-color: #fff;
      color: $green;
    }
  }
  &_cancel {
    border: 1px solid #a9abae;
    &:hover {
      background-color: #ffc625;
      border: 1px solid #ffc625;
    }
  }
}
@media screen and (max-width: 540px) {
  .form {
    padding-top: 5vw;
    &__wrapper {
      padding: 0;
    }
    &__container {
      flex-direction: column;
      align-items: center;
      &:not(:last-child) {
        margin-bottom: 3vw;
      }
    }
    &__left-side,
    &__right-side {
      flex-basis: unset;
    }
    &__left-side {
      margin-right: unset;
      margin-bottom: 1vw;
      line-height: 24px;
    }
    &__right-side {
      width: 100%;
      max-width: 90vw;
    }
    #currency {
      margin-left: 3vw;
    }
    input[type="range"] {
      width: 80%;
    }
    &__buttons-container {
      margin-top: 5vw;
      padding: 3vw 0;
      justify-content: center;
    }
  }
  .btn {
    margin-right: unset;
    &:first-child {
      margin-right: 7vw;
    }
  }
}
</style>