<template>
  <div class="page flex">
    <div class="field">
      <label for="selectExample"></label>
      <InfoTooltip
        message="Choix de 3 possibilités, compliqué !"
        type="hoverSpan"
      >
        <select id="selectExample" name="choice">
          <option value="1">Choice 1</option>
          <option value="2">Choice 2</option>
          <option value="3">Choice 3</option>
        </select>
      </InfoTooltip>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'IndexPage',
})
</script>

<style lang="scss">
.page {
  @apply flex w-2/4 mx-auto justify-center;
  .field {
    @apply mt-5;
  }
}
</style>
