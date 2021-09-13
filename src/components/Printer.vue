<template>
  <label>What type of printer are you submitting a ticket for?</label>
  <select v-model="printerType">
    <option value="receipt">Receipt Printer</option>
    <option value="label">Label Printer</option>
    <option value="computer">Computer Printer</option>
  </select>

  <div v-if="printerType === 'receipt'">
    <p>Receipt Chosen</p>
  </div>

  <div v-if="printerType === 'label'">
    <p>Label Chosen</p>
  </div>

  <div v-if="printerType === 'computer'">
    <p>Computer Chosen</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      printerType: ''
    }
  }

}
</script>

<style>

</style>