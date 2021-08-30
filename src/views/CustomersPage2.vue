<template>
  <div>
    <h1>List of Customers Page 2/2</h1>
    <ul>
      <li v-for="customer in customersList" :key="customer.id">
        {{ displayName(customer) }}
        <button>
        <router-link :to="{name: 'CustomerFiche',
                           params: {id: customer.id,
                           customer: customer
                           }}"
        >Voir la fiche
        </router-link>
        </button>
        <button>
          Editer
        </button>
        <button>
          Supprimer
        </button>
      </li>
    </ul>
    <router-link to="/customers"><button>Page 1</button></router-link>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "CustomersPage2",
  data() {
    return {
      customersList: []
    }
  },
  methods: {
    displayName(customer) {
      return customer.firstName + ' ' + customer.lastName
    }
  },
  created() {
    axios
        .get('https://heroku-campus-suppliers.herokuapp.com/api/customers?page=2')
        .then(response => this.customersList = response.data.data)
  }
}
</script>

<style scoped>

</style>