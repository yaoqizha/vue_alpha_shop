<template>
  <main id="main-content" class="mt-4">
    <div class="main__title-wrapper container">
      <h2 class="main-title">結帳</h2>
    </div>
    <div class="main__content-wrapper container">
      <!-- stepper -->
      <Processor />
    </div>
  </main>
</template>
<script>
import Processor from "./../components/Processor.vue";
export default {
  components: {
    Processor,
  },
};
</script>

<style lang="scss">

main {
  .container {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr 540px 125px 445px 1fr;
  }

  .main-title {
    margin-bottom: 48px;
    grid-column: 2/5;
  }
  .main__content-wrapper {
    height: 468px;
  }
}
</style>