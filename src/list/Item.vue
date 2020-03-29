<template>
  <div class="listr-item">
    <span class="listr-item-label">{{ item.label }}</span>
    <ReserveButton v-on:click="handleClick" />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import ReserveButton from './ReserveButton.vue'
import { ItemData } from './list-api'

@Component({
  components: {
    ReserveButton
  }
})
export default class Item extends Vue {
  @Prop({ default: null })
  item!: ItemData | null;

  handleClick () {
    this.$emit('reserve', this.item)
  }
}
</script>

<style lang="scss"></style>
