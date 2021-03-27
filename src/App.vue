<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div v-for="(item, i) in pendingOrders" :key="i">
      <Order />
    </div>
  </div>
</template>

<script>

import Order from './components/Order'

export default {
  name: 'App',
  components: {
    Order
  },
  data () {
    return {
      pendingOrders: [],
      assignedOrders: []
    }
  },
  created () {
    this.fetchPending()
    this.fetchAssigned()
  },
  methods: {
    async fetchPending (){
      try {
        const resp = await fetch('https://api.stagingtahmeelapp.com/technical_interview/orders/pending')
        const data = await resp.json()
        this.pendingOrders = data.pending_orders
      } catch (error) {
        console.log('error: ', error);
      }
    },
    async fetchAssigned () {
      try {
        const resp = await fetch('https://api.stagingtahmeelapp.com/technical_interview/orders/assigned')
        const data = await resp.json()
        this.assignedOrders = data.assigned_orders
      } catch (error) {
        console.log('error: ', error);
      }
    }
  }
}
</script>

