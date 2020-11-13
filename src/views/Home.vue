<template>
  <div>
  <v-data-table :headers="headers" :items="user" item-key="email" v-model="table1"></v-data-table>
    <v-btn @click="table1 = !table1" >Visualizar</v-btn>
  </div>  
</template>



<script>
import firebase from 'firebase' 
import {db} from '../service/firebase'

export default {
  data: () => ({
    
    name: null,
    email: null,     
    telefone: null,
    userFinal: null,
    table1: false,
    
    

    // cabeçalho da tabela
    headers: [
      {
        text: "Nome",
        align: "center",
        value: "name",
      },
      {
        text: "Telefone",
        align: "center",
        value: "telefone",
      },
      {
        text: "E-mail",
        align: "center",
        value: "email",
      },
    ]
    
  }),
  methods: {
    showUserList() {
      table1.items == "user"
      
      
    }
  },
  computed: {
      headersList() {
        return this.headers
      },
      userList() {
        return this.user
      }
  },
  
    
  async created() {
    var userData = [];
    var user = ""
    await db.collection("users").get().then((querySnapshot) => {
      querySnapshot.docs.forEach((doc) => {
        let data = doc.data();
        this.name = data.name;
        this.telefone = data.telefone;
        this.email = data.email;
        userData.push(data);
        
        
      });
       this.user = userData;      
       console.log(this.user)
       

     
    });
  },
  
}


</script>