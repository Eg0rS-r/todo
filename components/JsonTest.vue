<template>
  <div class="Test">
    <h2>Json Test</h2>
    <button class="btn btn-primary" type="submit" @click="addItem">Add</button>
    <button class="btn btn-primary" type="submit" @click="delItem">Del</button>
    <button class="btn btn-primary" type="submit" @click="saveList">Save?</button>
    <button class="btn btn-primary" type="submit" @click="getList">Get?</button>
    <ul>
      <li v-for="item in itemList" :key="item">{{item}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
      itemList: [],
    };
  },
  methods: {
    addItem() {
      this.count++
      this.itemList.push('Element ' + this.count)
    },
    delItem() {
      this.count--
      this.itemList.pop()
    },
    saveList() {
      localStorage.setItem('itemList', JSON.stringify(this.itemList));
      console.log("save list")
    },
    getList() {
      this.itemList = JSON.parse(localStorage.getItem('itemList'))
      console.log("get list")
    }
  }
};
</script>

<style lang="scss">
</style>