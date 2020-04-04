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
import { Component, Vue, Prop, Watch } from 'vue-property-decorator'
import Item from './Item.vue'
import { getList, ListData, ItemData, reserve, cancel, Unsubscribe, subscribe } from './list-api'

@Component({
  components: {
    Item
  }
})
export default class List extends Vue {
  @Prop({ default: '' })
  name!: string

  list: ListData | null = null;
  unsubscribe: Unsubscribe | null = null;

  @Watch('name')
  onNameChange () {
    this.initList()
  }

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

  async initList () {
    await this.loadList()

    if (this.unsubscribe !== null) {
      this.unsubscribe()
    }

    this.unsubscribe = subscribe(this.name, () => this.loadList())
  }

  async loadList () {
    this.list = await getList(this.name)
  }

  async created () {
    this.initList()
  }
}
</script>

<style lang="scss">
</style>
