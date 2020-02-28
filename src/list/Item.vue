<template>
  <div class="listr-item">
    <span class="listr-item-label">{{ label }}</span>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'

// Define the component in class-style
@Component
export default class Item extends Vue {
  @Prop({ default: '' })
  label!: string;
}
</script>

<style lang="scss">
</style>
