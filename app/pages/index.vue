<template>
  <div class="page flex">
    <div class="fields">
      <InfoTooltip
        message="Choix de 3 possibilités, compliqué !"
        type="hoverSpan"
        position="bottom"
      >
        <select id="selectExample" name="choice">
          <option value="1">Choice 1</option>
          <option value="2">Choice 2</option>
          <option value="3">Choice 3</option>
        </select>
      </InfoTooltip>

      <InfoTooltip
        message="Exemple de tooltip sur le haut"
        type="focus"
        position="top"
        class="mt-20"
        target-element="input-name"
      >
        <input
          id="input-name"
          type="text"
          class="border-2 rounded-lg bg-gray-200 border-gray-200"
          placeholder="Haut (focus)"
        />
      </InfoTooltip>

      <InfoTooltip
        message="Exemple de tooltip sur la droite"
        type="hover"
        position="right"
        class="mt-20"
      >
        <input
          id="input-name"
          type="text"
          class="border-2 rounded-lg bg-gray-200 border-gray-200"
          placeholder="Droite (hover)"
        />
      </InfoTooltip>

      <InfoTooltip
        message="Exemple de tooltip sur la gauche"
        type="hover"
        position="left"
        class="mt-20"
      >
        <input
          id="input-name"
          type="text"
          class="border-2 rounded-lg bg-gray-200 border-gray-200"
          placeholder="Gauche (hover)"
        />
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
  @apply flex max-w-min mx-auto justify-center;
  .fields {
    @apply mt-20;
  }
}
</style>
