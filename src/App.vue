<template>
  <div id="app">
    <input type="text" v-model="listName" />
    <List v-bind:name="listName" />
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
export default class App extends Vue {
  listName = 'My List'
}
</script>

<style lang="scss">
</style>
