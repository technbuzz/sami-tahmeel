<template>
  <div id="app">
    <v-app>
      <v-container>
        <v-row>
          <v-col>
            <div v-for="(item, i) in pendingOrders" :key="i">
              <Order :order="item" />
            </div>
          </v-col>
          <v-col>
            <h2>Assigned Orders</h2>


          </v-col>
        </v-row>
      </v-container>
    </v-app>
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

<style>
  #app {
    background-color: #2a2a2a;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }
</style>

