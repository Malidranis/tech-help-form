<template>
  <form>
      <h1>Support Ticket</h1>

      <div v-if="intro">
        <p>Welcome to the Company Support Portal. Are you submitting a ticket on behalf of another employee?</p>
        <button @click="forMyself">No</button>
        <button @click="forAnother">Yes</button>
      </div>

      <div v-if="another">
          <label>Please enter the name and email of the person you are crating this ticket for.</label>
          <label>Name:</label>
          <input type="text" required v-model="name">
          <label>Email:</label>
          <input type="email" required v-model="email">
      </div>

      <div v-if="formStart">
          <label>What type of issue do you need assistance with?</label>
          <select v-model="requestType">
              <option value="wifi">Wireless Access</option>
              <option value="printer">Printer Setup/Issue</option>
              <option value="software">Software Install/Update</option>
              <option value="hardware">Device Malfunctioning</option>
          </select>
      </div>

      <Wifi v-if="requestType === 'wifi'" />
      <Printer v-if="requestType === 'printer'" />
      <Software v-if="requestType === 'software'" />
      <Hardware v-if="requestType === 'hardware'" />

      <button @click="submitForm" v-if="formStart">Submit Ticket</button>

      <Submitted v-if="formSubmitted" />
      
  </form>
</template>

<script>
import Wifi from './Wifi.vue'
import Printer from './Printer.vue'
import Software from './Software.vue'
import Hardware from './Hardware.vue'
import Submitted from './Submitted.vue'

export default {
    components: {Wifi, Printer, Software, Hardware, Submitted},
    data() {
        return {
            intro: true,
            formStart: false,
            another: false,
            name: '',
            email: '',
            requestType: '',
            formSubmitted: false           
        }
    },
    methods: {
        forMyself() {
            this.intro = false
            this.formStart = true
        },
        forAnother() {
            this.intro = false
            this.another = true
            this.formStart = true            
        },
        submitForm() {
            this.requestType = ''
            this.formSubmitted = true
        }
    }
}
</script>

<style>
    form {
        max-width: 420px;
        margin: 30px;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
    }
    label {
        color: #aaa;
        display: inline-block;
        margin: 25px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }
    input {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }
</style>