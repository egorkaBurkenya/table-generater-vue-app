<template class="form">
    <h3>create table</h3>
    <input class="table-name" type="text" v-model="tableName" placeholder="tableName" />
    <div class="inputs">
        <button class="add-column" @click="addInput()">add column</button>
        <input 
            class="column"
            v-for="(input, i) in inputs" 
            type="text" 
            placeholder="name"
            v-model="input.name"
            :key="i"/>
    </div>
    <button class="create-table" @click="createTable()">add table</button>
    <hr />
</template>

<script>

export default {
  name: 'createForm',
  props: ["tools"],
  components: {},
  data() {
      return {
          tableName: "",
          inputs: []
      }
  },
  methods: {
      createTable() {
          let fields = [];
          for (let i in this.inputs) {
            fields.push(this.inputs[i].name)
          }
          if (this.tableName != "") {
                this.tools.addNewTable(this.tableName, fields);
                this.tableName = "";
                this.inputs = [];
          } else alert("сначала укажи название")
      },
      addInput() {
              this.inputs.push({
                  name: ""
              })
              this.columnName = "";
      }
  }
}
</script>

<style>
.create-table{
   font-size: 16px;
    width: 150px;
    margin: 0 auto;
    margin-top: 10px;
    background-color: green;
    color: #fafafa;
    border-radius: 3px; 
}
.column {
    border: 2px solid green;
    border-radius: 3px;
    padding: 3px;
    font-size: 16px;
    margin-top: 5px;
}
.add-column {
    border-radius: 3px; 
    font-size: 16px;
    width: 150px;
    margin: 0 auto;
    margin-top: 10px;
}
.table-name {
    border: 2px solid green;
    border-radius: 3px;
    padding: 3px;
    font-size: 16px;
}
.inputs{
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    width: 300px;
    }
</style>
