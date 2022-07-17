<template>
  <div class="form__panel">
    <div class="form-container">
      <form action="" id="form" class="form">
        <div id="step1" class="part" v-bind:class="{ 'd-none': step !== 1 }">
          <div class="part-title my-6">寄送地址</div>
          <div class="form__row form__row--double">
            <label for="">稱謂</label>
            <div class="select-wrapper">
              <select name="user-title" id="user-title">
                <option value="">先生</option>
                <option value="">女士</option>
              </select>
            </div>
            <label for="">姓名</label
            ><input id="user-name" type="text" placeholder="請輸入姓名" />
          </div>
          <div class="form-wrapper">
            <div class="form__row">
              <label for="">電話</label
              ><input
                id="user-phone"
                type="text"
                placeholder="請輸入行動電話"
              />
            </div>
            <div class="form__row">
              <label for="">Email</label
              ><input id="user-mail" type="text" placeholder="請輸入電子郵件" />
            </div>
          </div>
          <div class="form-wrapper">
            <div class="form__row">
              <label for="">縣市</label>
              <div class="select-wrapper">
                <select name="user-location" id="user-location">
                  <option value="" disabled selected>請選擇縣市</option>
                  <option value="">臺北</option>
                  <option value="">臺中</option>
                  <option value="">臺南</option>
                  <option value="">臺東</option>
                  <option value="">南投</option>
                </select>
              </div>
            </div>
            <div class="form__row">
              <label for="">地址</label>
              <input id="user-address" type="text" placeholder="請輸入地址" />
            </div>
          </div>
        </div>
        <div id="step2" class="part" v-bind:class="{ 'd-none': step !== 2 }">
          <div class="part-title my-6">運送方式</div>
          <div class="form__row">
            <div class="form__btn--shipway">
              <div class="radio-wrapper">
                <input
                  name="shipway"
                  type="radio"
                  value="standard"
                  @click="$emit('normal-ship')"
                  checked
                />
              </div>
              <div class="form__btn--shipway-description">
                <div class="ship-method">標準運送</div>
                <div class="ship-time">約3~7個工作天</div>
              </div>
              <div class="form__btn--shipway-fee">免費</div>
            </div>
          </div>
          <div class="form__row">
            <div class="form__btn--shipway">
              <div class="radio-wrapper">
                <input
                  name="shipway"
                  type="radio"
                  value="DHL"
                  @click="$emit('dhl-ship')"
                />
              </div>
              <div class="form__btn--shipway-description">
                <div class="ship-method fw-700">DHL貨運</div>
                <div class="ship-time">48小時內送達</div>
              </div>
              <div class="form__btn--shipway-fee">$ 500</div>
            </div>
          </div>
        </div>
        <div id="step3" class="part" v-bind:class="{ 'd-none': step !== 3 }">
          <div class="part-title my-6">付款資訊</div>
          <div class="form__row">
            <label for="">持卡人姓名</label
            ><input id="card-name" type="text" placeholder="John Doe" />
          </div>
          <div class="form__row">
            <label for="">卡號</label
            ><input
              id="card-number"
              type="text"
              placeholder="1111 2222 3333 4444"
            />
          </div>
          <div class="form__row form__row--double">
            <label for="">有效期限</label>
            <input type="month" name="" id="" placeholder="MM/YY" />
            <label for="">cvc/ccv</label
            ><input id="cvc" type="text" placeholder="123" />
          </div>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    step: Number,
  },
};
</script>

<style lang="scss" scoped>
%input-style {
  height: 40px;
  border: 1px solid var(--input-border);
  border-radius: 5px;
  padding-left: 8px;
  font-size: 12px;
  color: var(--input-fc);
  background-color: #fff;
}

.form__panel {
  flex: 1;
  display: flex;
  flex-direction: column;

  .form {
    .form-wrapper {
      display: grid;
      width: 100%;
      grid-auto-flow: column;
      grid-gap: 8px 30px;
    }
    .part-title {
      font-weight: 700;
      font-size: 24px;
    }

    &__row {
      height: 64px;
      margin-bottom: 24px;
      display: flex;
      flex-flow: column nowrap;

      &--double {
        display: grid;
        width: 100%;
        grid-template-rows: 16px 40px;
        grid-auto-flow: column;
        grid-gap: 8px 30px;
      }

      label {
        margin-bottom: 8px;
        display: block;
        line-height: 16px;
        color: $form-label;
        font-size: 8px;
        font-weight: 700;
      }

      input {
        @extend %input-style;
        cursor: pointer;

        &[type="month"] {
        }
      }

      select {
        @extend %input-style;
        -webkit-appearance: none;
        width: 100%;
        cursor: pointer;
      }

      .select-wrapper {
        position: relative;
        z-index: 0;

        &::after {
          position: absolute;
          z-index: 0;
          right: 8px;
          top: 50%;
          transform: translateY(-50%);
          content: "";
          border-style: solid;
          border-width: 5px 4.5px 0 4.5px;
          border-color: var(--main-fc) transparent transparent transparent;
        }
      }
    }

    &__btn--shipway {
      height: 100%;
      display: flex;
      position: relative;
      border: 1px solid $pale-grey;
      border-radius: 4px;

      .radio-wrapper {
        display: flex;
      }

      input {
        width: 20px;
        height: 20px;
        padding: 0;
        margin: 0 20px;
        align-self: center;

        &[type="radio"] {
          -webkit-appearance: none;
          border-radius: 50%;
          cursor: pointer;

          &:checked {
            box-shadow: inset 0 0 0 6px var(--main-fc);
          }
        }
      }

      &-description {
        position: relative;
        width: 100%;
        height: 100%;

        .ship-method {
          position: absolute;
          top: 20%;
          line-height: 20px;
          font-weight: 400;
          font-size: 14px;
        }

        .ship-time {
          position: absolute;
          bottom: 20%;
          line-height: 16px;
          font-weight: 400;
          font-size: 12px;
        }

        .fw-700 {
          font-weight: 700;
        }
      }

      &-fee {
        position: absolute;
        right: 20px;
        top: 15%;
        font-weight: 400;
        font-size: 12px;
        line-height: 16px;
      }
    }

    .ship-active {
      border-color: var(--main-fc);
    }
  }
}
</style>