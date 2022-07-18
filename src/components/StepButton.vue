<template>
  <div id="btn-control" class="control__panel">
    <button
      class="control__panel--back"
      v-bind:class="{ 'v-hidden': step === 1 }"
      @click="$emit('minus-step')"
    >
      上一步<span class="arrow back-arrow">←</span>
    </button>
    <button class="control__panel--next" @click="$emit('add-step')">
      {{ step === 3 ? "確認下單" : "下一步" }}
      <span
        class="next-arrow"
        v-bind:class="{ 'd-none': step === 3, arrow: step !== 3 }"
        >→</span
      >
    </button>
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
  methods: {
    addStep() {
      this.$emit("add-step");
    },
    minusStep() {
      this.$emit("minus-step");
    },
  },
};
</script>
<style lang="scss" scoped>
.v-hidden {
  visibility: hidden;
}
%control-button-style {
  width: 100%;
  height: 46px;
  display: inline-block;
  border-radius: 8px;
  border: 0 solid var(--btn-next);
  background-color: var(--btn-next);
  color: white;
}
.control__panel {
  display: flex;
  justify-content: space-between;
  &--next {
    width: 174px;
    height: 46px;
    margin-bottom: 0;
    display: inline-block;
    border-radius: 8px;
    border: 0 solid $btn-next;
    background-color: #f67599;
    color: white;
  }

  &--back {
    @extend %control-button-style;
    color: var(--control-fc);
    background-color: var(--control-btn);
    padding-left: 0;
    text-align: left;
    width: 174px;
  }

  .arrow {
    margin-left: 13.5px;
    display: inline-block;
    font-size: 20px;
  }
}
</style>