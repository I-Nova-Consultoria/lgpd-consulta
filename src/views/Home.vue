<template>
  <v-data-table :headers="headers" :items="user" item-key="email"></v-data-table>
</template>

<script>
import firebase from 'firebase' 
import {db} from '../service/firebase'

export default {
  data: () => ({
    
    name: null,
    email: null,     
    telefone: null,
    
    

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
         this.user = userData;      
      console.log(this.user)
      });

     
    });
  },
}

</script>