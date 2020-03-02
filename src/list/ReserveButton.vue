<template>
  <button v-on:click="handleClick">Reserve</button>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class ReserveButton extends Vue {
  handleClick() {
    this.$emit("click");
  }
}
</script>

<style lang="scss">
</style>
