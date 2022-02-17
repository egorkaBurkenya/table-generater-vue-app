<template>
  <h2 class="main">table application</h2>
  <createTable class="create-table" :tools="tools" />
  <Tabs :tools="tools" :tabs="tables" />
</template>

<script>

import Tabs from "./components/Tabs.vue";
import createTable from "./components/createTable.vue";

export default {
  name: 'App',
  components: {Tabs, createTable},
  data() {
    return {
      tableName: "",
      tables: this.getTablesFromLocalStorage(),
      tools: {addNewTable: this.addNewTable, addValues: this.addValues}
    }
  },
  methods: {
    addValues(values, tableNumber) {
      this.tables[tableNumber].values.push(values)
      console.log(this.tables);
      localStorage.tables = JSON.stringify(this.tables)
    },
    addNewTable(name, fields) {
      // console.log(name, fields);
      this.tables.push({
        name,
        fields,
        values: []
        })
      console.log(this.tables);
      localStorage.tables = JSON.stringify(this.tables)
    },
    getTablesFromLocalStorage() {
      console.log(localStorage.tables[0]);
      return localStorage.tables ? JSON.parse(localStorage.tables) : [{
        name: "example",
        fields: ["col1", "col2", "col3"],
        values: [[1, 2, 3], ['a', 'b', 'c']]
        }]
  }
  }
}
</script>

<style>
.tabs {
  display: flex;
}
.tab {
  border: 1px solid gray;
  padding: 3px;
  border-radius: 3px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
