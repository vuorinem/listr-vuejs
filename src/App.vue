<template>
  <div id="app">
    <List name="My List" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import List from './list/List.vue'

@Component({
  components: {
    List
  }
})
export default class App extends Vue {}
</script>

<style lang="scss">
</style>
