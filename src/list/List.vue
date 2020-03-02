<template>
  <div class="listr-list">
    <h1>{{ name }}</h1>
    <Item
      v-for="(item, index) in items"
      v-bind:key="item"
      v-bind:label="item"
      v-on:reserve="handleReserve(index)"
      />
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import Item from './Item.vue'

const TestItems = [
  'First item',
  'Second item',
  'Third item'
]

@Component({
  components: {
    Item
  }
})
export default class List extends Vue {
  @Prop({ default: '' })
  name!: string

  items = TestItems

  handleReserve (itemIndex: number) {
    alert(`Reserved '${TestItems[itemIndex]}'`)
  }
}
</script>

<style lang="scss">
</style>
