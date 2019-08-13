<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <p>{{ JSON.stringify(set) }}</p>
    <button @click="addSet">ADD</button>
    <ul>
      <li v-for="(row, index) of n" :key="index" v-text="row"></li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Watch } from "vue-property-decorator";

@Component({})
export default class Home extends Vue {
  private set: any = new Set();
  private n: number = 0;

  @Watch("set")
  setChange(val: any, oldVal: any) {
    console.log(val, "--", oldVal);
  }

  addSet() {
    ++this.n;
    this.set.add(this.n);
  }
}
</script>

<style lang="less" scoped>
button {
  user-select: none;
}
li {
  list-style: none;
}
</style>
