<template>
  <v-card
    dark
    class="mb-5"
    max-width="374"
  >
    <v-card-text class="my-0 py-2" id="card-header">
      <v-row justify="space-between">
        <v-col>
          <div class="text-uppercase font-weight-light">ref/po</div>
          <strong>{{ order.load_ref}}</strong>
        </v-col>
        <v-spacer></v-spacer>
        <v-col>
          <div class="text-uppercase font-weight-light">
            <slot></slot>
          </div>

          <strong>{{ month }} </strong>
        </v-col>
      </v-row>
    </v-card-text>
    <v-divider></v-divider>
    <v-card-text id="card-body">
      <v-row
        align="center"
        class="mx-0 justify-center"
      >
        <div class="ml-4">
          <strong> Order: {{ order.order_number }} </strong>
        </div>
      </v-row>

      <v-row
        align="center"
        class="mx-0 justify-center"
      >
        <div class="ml-4">
          <div class="text-uppercase font-weight-light">CreatedAt:</div>
          <strong>{{ createdDate }}</strong>
        </div>
      </v-row>

      <v-row>
        <v-col>
          <div class="text-uppercase font-weight-light">Customer Name</div>
          <strong>{{ order.customer_name }}</strong>

          <div class="text-uppercase font-weight-light mt-2">Price to Customer</div>
          <strong>123.00 AED</strong>
        </v-col>
        <v-col>
          <div class="text-uppercase font-weight-light">Phone Number</div>
          <strong>{{ order.phone_number }}</strong>

          <div class="mt-2 text-uppercase font-weight-light">Tahmeel Fee</div>
          <strong>{{ order.order_price_formatted }}</strong>
        </v-col>
      </v-row>
    </v-card-text>
  </v-card>

</template>

<script>
export default {
  name: 'Order', 
  props: [ 'order' ],
  computed: {
    createdDate () {
      const options = {
        day: 'numeric',
        month: '2-digit',
        hour: 'numeric', minute: 'numeric', hour12: false
      };
      return this.formatDate(options)
    },
    month () {
      const options = {
        day: 'numeric',
        month: 'long',
      };
      return this.formatDate(options)
    }
  },
  methods: {
    formatDate (options) {
      const date = new Date(this.order.created_at)
      const result = Intl.DateTimeFormat('en-GB', options).format(date)
      return result.split(',').join('')
    }
  }
}
</script>

<style lang="scss">

  .mb-2 {
    margin-bottom: 8px;
  }

  #card-header {
    background-color: #fff;
    color: #666;
  }

  #card-body{ 
    background: #545454
  }
</style>