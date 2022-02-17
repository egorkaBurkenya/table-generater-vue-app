<template>
  <div class="tabs">
    <div 
    v-for="(tab, i) in tabs" 
    :class="(i == this.selectTabIndex) ? 'tab select' : 'tab'"
    :key="i">
      <tab  @click="selectTab(i)" :name="tab.name" :data="tab" />
    </div>
  </div>
<Table :tools="tools" :data="tabs[selectTabIndex]" :i="selectTabIndex"/>
</template>

<script>
import Tab from "./Tab.vue";
import Table from "./Table.vue";
export default {
  name: 'Tabs',
  props: ["tabs", "tools"],
  components: {Tab, Table},
  data() {
    return {
        selectTabIndex: 0
    }  
  },
  methods: {
      selectTab(i) {
          this.selectTabIndex = i;
      }
  }
}
</script>

<style>
.select {
    background-color: gray;
    color: #fafafa;
}
.tabs {
  display: flex;
}
.tab {
  border: 1px solid gray;
  padding: 3px;
  border-radius: 3px;
  cursor: pointer;
}
</style>
