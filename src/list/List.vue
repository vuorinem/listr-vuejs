<template>
  <div class="listr-list">
    <h1>{{ name }}</h1>
    <div v-if="!!list">
      <Item
        v-for="(item, index) in list.items"
        v-bind:key="index"
        v-bind:item="item"
        v-on:reserve="handleReserve"
        />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import Item from './Item.vue'
import { getList, ListData, ItemData } from './list-api'

@Component({
  components: {
    Item
  }
})
export default class List extends Vue {
  @Prop({ default: '' })
  name!: string

  list: ListData | null = null;

  handleReserve (item: ItemData) {
    alert(`Reserved '${item.label}'`)
  }

  async loadList () {
    this.list = await getList(this.name)
  }

  async created () {
    this.loadList()
  }
}
</script>

<style lang="scss">
</style>
