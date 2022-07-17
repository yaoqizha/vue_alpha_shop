<template>
  <div id="step-control" class="stepper__panel">
    <div class="stepper__panel--container">
      <div class="stepper__panel__step">
        <div class="stepper__panel__step--pc">
          <div
            class="stepper__panel__step--circle left"
            v-bind:class="{ active: step === 1, checked: step > 1 }"
          ></div>
          <div class="stepper__panel__step--label address">寄送地址</div>
        </div>
      </div>
      <div class="stepper__panel__step">
        <div class="stepper__panel__step--pc center">
          <div
            class="stepper__panel__step--circle middle"
            v-bind:class="{ active: step === 2, checked: step > 2 }"
          ></div>
          <div class="stepper__panel__step--label shipway">運送方式</div>
        </div>
        <span class="connect-line before"></span>
      </div>
      <div class="stepper__panel__step">
        <div class="stepper__panel__step--pc">
          <div
            class="stepper__panel__step--circle right"
            v-bind:class="{ active: step === 3 }"
          ></div>
          <span class="connect-line after"></span>
          <div class="stepper__panel__step--label payinfo">付款資訊</div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  },
  props: {
    step: Number,
  },
};
</script>
<style lang="scss" scoped>
@mixin getStepNums($num) {
  @for $i from 1 through $num {
    &:nth-child(#{$i}) .stepper__panel__step--circle::after {
      content: "#{$i}";
    }
  }
}
.stepper__panel {
  grid-column: 2/3;
  height: 1.5rem;
  width: 100%;
  margin-top: 0;
  &--container {
    display: flex;
  }

  &__step {
    flex: 1;
    position: relative;
    width: 100%;
    margin: 0 auto;
    text-align: center;
    @include getStepNums(3);
    line-height: 1.5rem;

    &--pc {
      height: 100%;
      &.center {
        display: flex;
        margin: 0 auto;
        width: fit-content;
      }
    }

    &--circle {
      margin: 0 auto;
      height: 24px;
      width: 24px;
      background-color: var(--main-bg);
      border: 1px solid $step-undone;
      border-radius: 50%;
      color: $step-undone;

      &::after {
        font-size: 8px;
        @include alignCenter();
      }

      &.middle {
        margin: 0 8px 0 0;
        position: relative;
      }

      &.right {
        position: absolute;
        right: 72px;
      }

      &.left {
        position: absolute;
        left: 0;
      }
    }

    .active,
    .checked {
      background-color: var(--step-done);
    }

    .stepper__panel__step--circle.checked::after {
      content: "\2714";
    }

    &--label {
      display: block;
    }

    .address {
      position: absolute;
      left: 32px;
      font-weight: 400;
    }

    .shipway {
      font-weight: 400;
    }

    .payinfo {
      position: absolute;
      right: 0;
      font-weight: 400;
    }

    .connect-line {
      position: absolute;
      top: 12px;
      display: block;
      height: 2px;
      width: 60%;
      background-color: $pale-grey;

      &.before {
        left: -43%;
      }

      &.after {
        right: 57%;
      }
    }
  }
}
</style>