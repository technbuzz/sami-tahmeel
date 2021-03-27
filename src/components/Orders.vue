<template>
  <v-row justify="center">
    <v-col cols="12" sm="6" md="4">
      <v-expansion-panels accordion :value="panel">
        <v-expansion-panel>
          <v-expansion-panel-header class="order">
            <template v-slot:actions>
                <v-icon class="icon">$expand</v-icon>
            </template>
            <v-spacer class="order-spacer"></v-spacer>
            <span class="header text-uppercase">Pending</span>
            <v-badge class="badge justify-end" color="#70D6C1" inline :content="pending.length"></v-badge>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <div v-for="(item, i) in pending" :key="i">
              <Order :order="item"><v-spacer></v-spacer></Order>
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
            <v-badge class="badge justify-end" color="#70D6C1" inline :content="assigned.length"></v-badge>
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <div v-for="(item, i) in assigned" :key="i">
              <Order :order="item">To Pickup</Order>
            </div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-col>
  </v-row>
  
</template>


<script>
import Order from './Order'

export default {
  name: 'Orders',
  components: {
    Order
  },
  props: ['pending', 'assigned'],
  created () {
    // open the first panel of accordion after 500ms
    setTimeout(() => {
      this.panel = 0
    }, 500);
  },
  data () {
    return {
      panel: null
    }
  }
}
</script>

<style lang="scss">
  $badge-min-width: 30px;

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