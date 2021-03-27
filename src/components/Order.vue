<template>
  <v-card
    dark
    class="mb-2"
    max-width="374"
  >
    <v-card-title light>{{ order.customer_name }}</v-card-title>
    <v-divider></v-divider>
    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >

        <div class="grey--text ml-4">
          <strong> Order: {{ order.order_number }} </strong>
        </div>
      </v-row>

      <v-row
        align="center"
        class="mx-0"
      >
        <div class="grey--text ml-4">
          <p class="term">CreatedAt:</p>
          <strong>{{ order.created_at }}</strong>
        </div>
      </v-row>

      <v-row>
        <v-col>
          <p class="term">Customer Name</p>
          <strong>{{ order.customer_name }}</strong>

          <p class="term">Price to Customer</p>
          <!-- {{ order.}} -->
        </v-col>
        <v-col>
          <p class="term">Phone Number</p>
          <strong>{{ order.phone_number }}</strong>

          <p class="term">Tahmeel Fee</p>
          <strong>{{ order.tahmeel_fee_in_cents }}</strong>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>

</template>

<script>
export default {
  name: 'Order', 
  props: [ 'order' ],
  created() {
    console.log(this.order)
  }
}
</script>

<style>
  .mb-2 {
    margin-bottom: 8px;
  }
  .term {
    font-size: small;
    text-transform: uppercase;
  }
</style>