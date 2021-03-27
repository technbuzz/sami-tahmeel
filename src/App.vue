<template>
  <div id="app">
    <v-app>
      <v-container>
        <Orders :pending="pendingOrders" :assigned="assignedOrders" />
      </v-container>
    </v-app>
  </div>
</template>
<script>

import Orders from './components/Orders'

export default {
  name: 'App',
  components: {
    Orders
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

<style>
  #app {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
</style>

