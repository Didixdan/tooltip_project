<template>
  <div id="tooltip-container">
    <span v-if="type == 'focus'" class="tooltip-content">
      <slot ref="input"></slot>
    </span>

    <span
      v-if="type == 'hover'"
      class="tooltip-content"
      @mouseover="show = true"
      @mouseleave="show = false"
    >
      <slot></slot>
    </span>

    <span v-if="type == 'hoverSpan'" class="tooltip-content">
      <slot></slot>
    </span>

    <div
      v-if="type == 'hoverSpan'"
      id="info-tooltip"
      @mouseover="show = true"
      @mouseleave="show = false"
    >
      ?
    </div>
    <div v-if="show" class="tooltip-message" :class="position">
      {{ message }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'InfoTooltip',
  props: {
    message: {
      type: String,
      default: '',
    },
    type: {
      type: String,
      default: '',
      enum: ['hover', 'hoverSpan', 'focus'],
    },
    position: {
      type: String,
      default: 'top',
    },
  },
  data() {
    return {
      show: false,
    }
  },
  mounted: () => {
    if (this.type === 'focus') {
      // bind the show of the tooltip with the focus
    }
  },
}
</script>

<style scoped lang="scss">
#tooltip-container {
  @apply relative;
  .tooltip-message {
    @apply absolute max-w-max min-w-min border-2 rounded-lg bg-gray-400 border-gray-400;
  }
  .top {
    @apply inset-x-0 -top-7 min-w-max;
  }
  .bottom {
    @apply -bottom-7 right-0 min-w-max;
  }
  .left {
    @apply inset-y-0 left-0;
  }
  .right {
    @apply inset-y-0 right-0;
  }
  #info-tooltip {
    @apply inline-block cursor-help text-center w-7 h-7 rounded-full border-2 bg-blue-300 border-blue-300;
  }
}
</style>
