<template>
  <v-row>
    <v-col>
      <v-expansion-panels accordion>
        <v-expansion-panel>
          <v-expansion-panel-header class="order">
            <template v-slot:actions>
                <v-icon class="icon">$expand</v-icon>
            </template>
            <v-spacer class="order-spacer"></v-spacer>
            <span class="header text-uppercase">Pending</span>
            <v-badge class="badge" color="#70D6C1" tile inline :content="pending.length"></v-badge>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <div v-for="(item, i) in pending" :key="i">
              <Order :order="item" />
            </div>
          </v-expansion-panel-content>
        </v-expansion-panel>
        <v-expansion-panel>
          <v-expansion-panel-header class="order">
            <template v-slot:actions>
                <v-icon class="icon">$expand</v-icon>
            </template>
            <v-spacer class="order-spacer"></v-spacer>
            <span class="header text-uppercase">Assigned</span>
            <v-badge class="badge" color="#70D6C1" tile inline :content="assigned.length"></v-badge>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <div v-for="(item, i) in assigned" :key="i">
              <Order :order="item" />
            </div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-col>
    <v-col></v-col>
  </v-row>
  
</template>


<script>
import Order from './Order'

export default {
  name: 'Orders',
  components: {
    Order
  },
  props: ['pending', 'assigned']
}
</script>

<style>
  .icon {
    order: 0;
  }
  .order-spacer{
    order: 1
  }
  .header {
    order: 2
  }

  .badge {
    order: 3
  }
</style>