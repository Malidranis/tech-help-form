<template>
  <label>Is this for a personal device or a work issued laptop?</label>
  <select v-model="deviceType">
      <option value="personal">Personal Device(Cell Phone/Tablet/Laptop)</option>
      <option value="work">Work Laptop</option>
  </select>

  <div v-if="deviceType === 'personal'">
      <label>We can help you get your personal device connected to the Wi-Fi. After submitting this ticket you will get an e-mail from Meraki with the instructions needed to connect your device.</label>
  </div>

  <div v-if="deviceType === 'work'">
      <label>We can connect to your laptop to the Wi-Fi. Please enter your device IP address, or MAC(Physical) Address.</label>
      <input type="text" v-model="ipMac">
      <button>Help me find my IP/MAC.</button>
  </div>
</template>

<script>
export default {
    data() {
        return {
            deviceType: '',
            ipMac: ''
        }
    }
}
</script>

<style>

</style>