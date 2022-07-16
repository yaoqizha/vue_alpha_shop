<template>
  <main id="main-content" class="mt-4">
    <div class="main__title-wrapper container">
      <h2 class="main-title">結帳</h2>
    </div>
    <div class="main__content-wrapper container">
      <div class="container--left">
        <!-- stepper -->
        <Processor />
        <!-- form -->
        <Form />
        <!-- line -->
        <div class="line"></div>
        <!-- button -->
        <StepButton />
      </div>
      <!-- shopping cart -->
      <ShoppingCart />
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