<template>
  <div class="listr-item">
    <span class="listr-item-label">{{ item.label }}</span>
    <span class="listr-item-count">({{ item.reservedCount }}/{{ item.count }})</span>
    <ReserveButton v-on:click="handleReserve" />
    <CancelButton v-on:click="handleCancel" />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import ReserveButton from './ReserveButton.vue'
import CancelButton from './CancelButton.vue'
import { ItemData } from './list-api'

@Component({
  components: {
    ReserveButton,
    CancelButton
  }
})
export default class Item extends Vue {
  @Prop({ default: null })
  item!: ItemData | null;

  handleReserve () {
    this.$emit('reserve', this.item)
  }

  handleCancel () {
    this.$emit('cancel', this.item)
  }
}
</script>

<style lang="scss"></style>
