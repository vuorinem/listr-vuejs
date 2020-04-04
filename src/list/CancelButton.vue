<template>
  <button v-on:click="handleClick">Cancel</button>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class CancelButton extends Vue {
  handleClick () {
    this.$emit('click')
  }
}
</script>

<style lang="scss">
</style>
