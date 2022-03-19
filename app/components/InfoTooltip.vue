<template>
  <div id="tooltip-container">
    <slot></slot>

    <div v-if="show && type !== 'hoverSpan'" class="tooltip-message">
      {{ message }}
    </div>

    <div
      v-if="type == 'hoverSpan'"
      id="info-tooltip"
      @mouseover="show = true"
      @mouseleave="show = false"
    >
      ?<span v-if="show" class="tooltip-message"> {{ message }} </span>
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
  },
  data() {
    return {
      show: false,
    }
  },

  methods: {
    showMessage: () => {
      this.show = true
    },
  },
}
</script>

<style scoped lang="scss">
#tooltip-container {
  .tooltip-message {
    @apply w-auto h-auto border-2 rounded-lg bg-gray-400 border-gray-400 absolute;
  }
  #info-tooltip {
    @apply inline-block cursor-help text-center w-7 h-7 rounded-full border-2 bg-blue-300 border-blue-300;
  }
}
</style>
