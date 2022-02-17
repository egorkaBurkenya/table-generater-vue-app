<template>
  <div>{{data.name}}</div>
    <div class="inputs">
        <input 
        type="text" class="input"
        v-for="(field, i) in data.fields"
        :placeholder="field"
        :key="i"
        v-model="fieldsValues[i]" />
    </div>
    <button @click="addValues()">add values</button>
  <table border="1">
    <tr>
        <th v-for="(field, i) in data.fields" :key="i">{{field}}</th>
    </tr>
    <tr v-for="(valueArr, i) in data.values" :key="i">
        <td v-for="(value, i) in valueArr" :key="i">{{value}}</td>
    </tr>
  </table>
</template>

<script>

export default {
  name: 'Table',
  props: ["data", "i", "tools"],
  components: {},
  data() {
      return {
          fieldsValues: {}
      }
  },
  methods: {
      addValues() {
          if (this.fieldsValues === {}) {
              alert("сначала заполните инпуты")
              return 
          }
          let arr = [];
          for (let e in this.fieldsValues) {
              arr.push(this.fieldsValues[e])
          }
          this.tools.addValues(arr, this.i)
          this.fieldsValues = {}
      }
  }
}
</script>

<style>
.inputs {
    display: flex;
}
</style>
