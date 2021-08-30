<template>
<div>
  <h2><span>Modification d'un customer</span></h2>
  <input type="text" v-model="form.firstName"/>
  <br>
  <input type="text" v-model="form.lastName"/>
  <br>
  <input type="email" v-model="form.email"/>
  <br>
  <input type="text" v-model="form.codepostal"/>
  <br>
  <input type="text" v-model="form.city"/>
  <br>
  <input type="text" v-model="form.address"/>
  <br>
  <input type="text" v-model="form.phoneNumber"/>
  <br>
  <input type="text" v-model="form.reseller_id"/>
  <br>
  <button @click="updateCustomer">Modifier le customer</button>
</div>
</template>

<script>
import axios from "axios";

export default {
  name: "CustomerEdit",
  props: {
    customer: Object
  },
  data() {
    return {
      form: {
        firstName: this.customer.firstName,
        lastName: this.customer.lastName,
        email: this.customer.email,
        codepostal: this.customer.codePostal,
        city: this.customer.city,
        address: this.customer.address,
        phoneNumber: this.customer.phoneNumber,
        reseller_id: this.customer.reseller_id
      }
    }
  },
  methods: {
    updateCustomer() {
      axios.put( 'https://heroku-campus-suppliers.herokuapp.com/api/customers/' + this.customer.id, {
        firstName: this.form.firstName,
        lastName: this.form.lastName,
        email: this.form.email,
        codePostal: this.form.codepostal,
        city: this.form.city,
        address: this.form.address,
        phoneNumber: this.form.phoneNumber,
        reseller_id: this.form.reseller_id
      })
    }
  }
}
</script>

<style scoped>

</style>