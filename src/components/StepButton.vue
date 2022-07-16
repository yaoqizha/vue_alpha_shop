<template>
  <div id="btn-control" class="control__panel">
    <button class="control__panel--back v-hidden">
      上一步<span class="arrow back-arrow">←</span>
    </button>
    <button class="control__panel--next">
      下一步 <span class="arrow next-arrow">→</span>
    </button>
  </div>
</template>
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