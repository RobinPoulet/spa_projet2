<template>
  <div class="customer">
    <router-link to="/customers">Revenir à liste des customers</router-link>
    <h1>{{ displayName(customer) }}</h1>
    <p>Email : {{ customer.email }}</p>
    <p>Adresse : </p>
    <span v-html="displayAddress(customer)"></span>
    <p>Numéro de reseller : {{ customer.reseller_id }}</p>
    <p>Créer le : {{ displayDate(customer.created_at) }}</p>
    <p>Dernière mise à jour : {{ displayDate(customer.updated_at) }}</p>
  </div>
</template>

<script>
export default {
  name: "CustomerFiche",
  props: {
    customer: Object
  },
  methods: {
    displayAddress(customer) {
      return customer.address + "<br>" + customer.codePostal + " " + customer.city
    },
    displayName(customer) {
      return customer.firstName + " " + customer.lastName
    },
    displayDate(string) {
      let date = new Date(string);
      return date.toLocaleString()
    }
  }
}
</script>

<style scoped>

</style>