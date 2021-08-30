<template>
  <div>
    <p>coucou</p>
    <h1>List of Customers Page {{ pageNumber }}/{{ totalPage }}</h1>

    <router-link to="/customers/add">Ajouter un nouveau customer</router-link>

    <ul>
      <li v-for="customer in customers" :key="customer.id">
        {{ displayName(customer) }}
        <button>
          <router-link :to="{name: 'CustomerFiche',
                           params: {id: customer.id,
                           customer: customer
                           }}"
          >Voir la fiche
          </router-link>
        </button>
        <router-link :to="{name: 'CustomerEdit', params: {id: customer.id, customer: customer}}">
          <button>
            Editer
          </button>
        </router-link>
        <button @click="deleteCustomer(customer.id)">
          Supprimer
        </button>
      </li>
    </ul>
    <button @click="getDataPreviousPage" v-show="pageNumber - 1 > 0">Page précédente</button>
    <button @click="getDataNextPage" v-show="pageNumber + 1 <= totalPage">Page Suivante</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: "Customers",
  data() {
    return {
      customers: [],
      pageNumber: 1,
      totalPage: 1
    }
  },
  methods: {
    displayName(customer) {
      return customer.firstName + ' ' + customer.lastName
    },
    getData() {
      axios
          .get('https://heroku-campus-suppliers.herokuapp.com/api/customers?page=' + this.pageNumber)
          .then(
              response => {this.customers = response.data.data, this.totalPage = response.data.last_page}
          )
    },
    getDataNextPage() {
      this.pageNumber += 1;
      this.getData();
    },
    getDataPreviousPage() {
      this.pageNumber -= 1;
      this.getData();
    },
    deleteCustomer(customerId) {
      axios.delete("https://heroku-campus-suppliers.herokuapp.com/api/customers/" + customerId);
      this.getData()
    }
  },
  created() {
    this.getData()
  }
}
</script>

<style scoped>

</style>