<script setup>
import KeyTable from './components/KeyTable.vue'
import Table from './components/Table.vue'
</script>

<template>
  <div id="app" v-if="!resetToggle">
    <h1>Inspect the elements to see which of them are updated on delete</h1>
    <h6>Updated elements flash with a blue light, when updated (Chrome)</h6>
    <br />
    <hr />
    <br />
    <div class="divider">
      <Table />
      <KeyTable />
    </div>
    <br />
    <hr />
    <br />
    <div class="button">
      <button @click="resetApp">Reset</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      resetToggle: false
    }
  },

  methods: {
    resetApp() {
      this.resetToggle = true;
      this.$nextTick(() => {
        this.resetToggle = false;
      })
    }
  }
}


</script>

<style scoped>
.divider {
  width: 100%;
  display: flex;
  justify-content: space-around;
  align-content: center;
  min-height: 180px;
}

.button {
  display: flex;
  justify-content: center;
}
</style>
