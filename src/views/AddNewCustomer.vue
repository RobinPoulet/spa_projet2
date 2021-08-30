<template>
  <div>
    <div v-show="userAdd">
      <p>L'Utilisateur a bien été ajouté</p>
      <router-link to="/customers/list">Retour à la liste des customers</router-link>
    </div>

    <div v-show="!userAdd">
    <h2><span>Ajout d'un customer</span></h2>
    <input type="text" v-model="form.firstName" placeholder="First Name"/>
    <br>
    <input type="text" v-model="form.lastName" placeholder="Last Name"/>
    <br>
    <input type="email" v-model="form.email" placeholder="Email"/>
    <br>
    <input type="text" v-model="form.codepostal" placeholder="Code Postal"/>
    <br>
    <input type="text" v-model="form.city" placeholder="City"/>
    <br>
    <input type="text" v-model="form.address" placeholder="Adress"/>
    <br>
    <input type="text" v-model="form.phoneNumber" placeholder="Phone Number"/>
    <br>
    <input type="text" v-model="form.reseller_id" placeholder="Reseller id"/>
    <br>
    <button @click="addNewCustomer">Ajouter le nouveau customer</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "AddNewCustomer",
  data() {
    return {
      form: {
        firstName: '',
        lastName: '',
        email: '',
        codepostal: '',
        city: '',
        address: '',
        phoneNumber: '',
        reseller_id: ''
      },
      userAdd : false
    }
  },
  methods: {
    addNewCustomer() {
      axios.post( 'https://heroku-campus-suppliers.herokuapp.com/api/customers', {
          firstName: this.form.firstName,
          lastName: this.form.lastName,
          email: this.form.email,
          codePostal: this.form.codepostal,
          city: this.form.city,
          address: this.form.address,
          phoneNumber: this.form.phoneNumber,
          reseller_id: this.form.reseller_id
      });
      this.userAdd = true
    }
  }
}
</script>

<style scoped>

</style>