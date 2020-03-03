<template>
  <div class="listr-item">
    <span class="listr-item-label">{{ label }}</span>
    <ReserveButton v-on:click="handleClick" />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import ReserveButton from './ReserveButton.vue'

@Component({
  components: {
    ReserveButton
  }
})
export default class Item extends Vue {
  @Prop({ default: '' })
  label!: string;

  handleClick () {
    this.$emit('reserve', this.label)
  }
}
</script>

<style lang="scss"></style>
