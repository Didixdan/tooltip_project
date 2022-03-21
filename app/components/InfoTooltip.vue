<template>
  <div id="tooltip-container">
    <div
      v-if="type == 'focus'"
      class="tooltip-content inline-block"
      @focusin="showToolip(true)"
      @focusout="showToolip(false)"
    >
      <slot></slot>
    </div>

    <span
      v-if="type == 'hover'"
      class="tooltip-content"
      @mouseover="showToolip(true)"
      @mouseleave="showToolip(false)"
    >
      <slot></slot>
    </span>

    <span v-if="type == 'hoverSpan'" class="tooltip-content">
      <slot></slot>
    </span>

    <div
      v-if="type == 'hoverSpan'"
      id="info-tooltip"
      @mouseover="showToolip(true)"
      @mouseleave="showToolip(false)"
    >
      ?
    </div>
    <div v-if="show" id="tooltip-message" :class="position">
      {{ message }}
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

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
    targetElement: {
      type: String,
      default: '',
    },
  },
  data() {
    return {
      show: false,
    }
  },
  methods: {
    showToolip(showMessage: boolean) {
      console.log('caca')
      const element: any = this
      Vue.set(element, 'show', showMessage)
      element.$nextTick(() => {
        if (showMessage) {
          const infoTooltip = element.$el.children['tooltip-message']
          const widthParent = element.$el.offsetWidth
          const heightParent = element.$el.offsetHeight
          const className = infoTooltip.className
          switch (className) {
            case 'left':
              infoTooltip.style.right = widthParent + 'px'
              break
            case 'right':
              infoTooltip.style.left = widthParent + 'px'
              break
            case 'top':
              infoTooltip.style.top = '-' + heightParent + 'px'
          }
        }
      })
    },
  },
}
</script>

<style scoped lang="scss">
#tooltip-container {
  @apply relative inline-block;
  #tooltip-message {
    @apply absolute min-w-max h-auto border-2 rounded-lg bg-gray-400 border-gray-400;
  }
  .top {
    @apply inset-x-0;
  }
  .left,
  .right {
    @apply inset-y-0;
  }
  #info-tooltip {
    @apply inline-block cursor-help text-center w-7 h-7 rounded-full border-2 bg-blue-300 border-blue-300;
  }
}
</style>
