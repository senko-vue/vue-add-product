<template>
  <div class="progress">
    <div
      class="progress-bar bg-info"
      role="progressbar"
      :style="{width: itemNumberPercentage + '%'}"
      aria-valuenow="50"
      aria-valuemin="0"
      aria-valuemax="100"
    >
    {{ itemNumber }}/10
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main'
export default {
  data() {
    return {
      itemNumber: 0,
      itemNumberPercentage: 0
    }
  },
  created() {
    eventBus.$on("productListChanged", (productListLenght) => {
      this.itemNumber = productListLenght;
      this.itemNumberPercentage = productListLenght * 10;
    })
  }
};
</script>

<style>
</style>