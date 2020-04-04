<template>
  <div class="listr-list">
    <h1>{{ name }}</h1>
    <div v-if="!!list">
      <Item
        v-for="(item, index) in list.items"
        v-bind:key="index"
        v-bind:item="item"
        v-on:reserve="handleReserve"
        v-on:cancel="handleCancel"
        />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-property-decorator'
import Item from './Item.vue'
import { getList, ListData, ItemData, reserve, cancel } from './list-api'

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
    if (!this.list) {
      return
    }

    reserve(this.list.name, item.label)
  }

  handleCancel (item: ItemData) {
    if (!this.list) {
      return
    }

    cancel(this.list.name, item.label)
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
