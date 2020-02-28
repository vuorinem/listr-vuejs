<template>
  <div id="app">
    <Item label="First Item" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import Item from './list/Item.vue'

@Component({
  components: {
    Item
  }
})
export default class App extends Vue {}
</script>

<style lang="scss">
</style>
