<template>
  <div :class="`arrow ${direction}`" @click="arrowClick(direction)">
    <span :class="`svg svg-arrow-${direction}`">
      <svg enable-background="new 0 0 14 26" height="26px" id="svg4-Layer_1" version="1.1" viewBox="0 0 14 26"
        width="14px" x="0px" xml:space="preserve" xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink" y="0px">
        <path v-if="direction == 'prev'"
          d="M13,26c-0.256,0-0.512-0.098-0.707-0.293l-12-12c-0.391-0.391-0.391-1.023,0-1.414l12-12c0.391-0.391,1.023-0.391,1.414,0s0.391,1.023,0,1.414L2.414,13l11.293,11.293c0.391,0.391,0.391,1.023,0,1.414C13.512,25.902,13.256,26,13,26z" />
        <path v-if="direction == 'next'"
          d="M1,0c0.256,0,0.512,0.098,0.707,0.293l12,12c0.391,0.391,0.391,1.023,0,1.414l-12,12c-0.391,0.391-1.023,0.391-1.414,0s-0.391-1.023,0-1.414L11.586,13L0.293,1.707c-0.391-0.391-0.391-1.023,0-1.414C0.488,0.098,0.744,0,1,0z" />
      </svg>
      <span class="alt sr-only" />
    </span>
  </div>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  props: {
    direction: String,
  },
  emits: ['arrowClick'],
  methods: {
    arrowClick(direction) {
      this.$emit('arrowClick', direction)
    }
  }
});
</script>

<style lang="scss" scoped>
.svg {
  position: relative;
  left: 0;
  width: 14px;
  height: 26px;
  fill: #fff;
  transition: left 0.2s ease;
}

.arrow {
  margin: -33px 0 0;
  padding: 20px;
  position: absolute;
  top: 50%;
  cursor: pointer;
  z-index: 3;

  &.prev {
    left: 275px;

    &:hover .svg {
      left: -10px;
    }
  }

  &.next {
    right: 30px;

    &:hover .svg {
      left: 10px;
    }
  }
}
</style>
