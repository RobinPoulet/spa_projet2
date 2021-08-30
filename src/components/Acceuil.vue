<template>
  <div >
    <h1>bonjours</h1>
    
    <router-link  to="/customers/list"><button @click="onCustomersListclick">Customers</button></router-link> |
    <router-link  to="/resellers" ><button @click="onResellersListclick">Resellers</button></router-link> |
    <router-link to="/suppliers"><button @click="onSupplierListclick">Suppliers</button></router-link>
  </div>
  
</template>

<script>


export default {
    name: 'Acceuil',
    methods:{
        onResellersListclick(){
           alert("vous allez voir les resellers")
           
        },
        onSupplierListclick(){
           alert("vous allez voir les Suppliers")
           
        },
        onCustomersListclick(){
           alert("vous allez voir les Customers")
           
        },
    }
}
   
</script>
