<template>
  <main id="main-content" class="mt-4">
    <div class="main__title-wrapper container">
      <h2 class="main-title">結帳</h2>
    </div>
    <div class="main__content-wrapper container">
      <div class="container--left">
        <!-- stepper -->
        <Processor :step="step" />
        <!-- form -->
        <Form
          :step="step"
          :shippingFee="shippingFee"
          @dhl-ship="setDHLShip"
          @normal-ship="setNormalShip"
        />
        <!-- line -->
        <div class="line"></div>
        <!-- button -->
        <StepButton :step="step" @add-step="addStep" @minus-step="minusStep" />
      </div>
      <!-- shopping cart -->
      <ShoppingCart :shippingFee="shippingFee" />
    </div>
  </main>
</template>
<script>
import Processor from "./../components/Processor.vue";
import Form from "./../components/Form.vue";
import StepButton from "./../components/StepButton.vue";
import ShoppingCart from "./../components/ShoppingCart.vue";
export default {
  components: {
    Processor,
    Form,
    StepButton,
    ShoppingCart,
  },
  data() {
    return {
      step: 1,
      shippingFee: 0,
    };
  },
  methods: {
    addStep() {
      if (this.step < 3) {
        this.step += 1;
      }
    },
    minusStep() {
      if (this.step > 1) {
        this.step -= 1;
      }
    },
    setDHLShip() {
      this.shippingFee = 500;
      console.log("d");
    },
    setNormalShip() {
      this.shippingFee = 0;
      console.log("n");
    },
  },
};
</script>

<style lang="scss">
.d-none {
  display: none;
}
main {
  .container {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 540px 125px 445px 1fr;
  }

  .container--left {
    grid-column: 2/3;
  }

  .main-title {
    margin-bottom: 48px;
    grid-column: 2/5;
  }
  .main__content-wrapper {
    height: 468px;
  }
  .line {
    width: 100%;
    height: 1px;
    margin-top: 24px;
    margin-bottom: 24px;
    background-color: $pale-grey;
  }
}
</style>