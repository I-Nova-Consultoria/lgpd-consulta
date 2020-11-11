<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">
            Nome
          </th>
          <th class="text-center">
            Telefone
          </th>
          <th class="text-left">
            Email
          </th>
          
        </tr>
      </thead>
      <tbody>
        <tr  v-for="(item, index) in user" v-bind:key="index" >
  <td v-for="(sort,i) in item" :key="i">{{ sort }}</td>
</tr>
          
          
        
        
      </tbody>
      
    </template>
  </v-simple-table>
</template>

<script>
import firebase from 'firebase' 
import {db} from '../service/firebase'


  export default {

    
    data () {   
      
      return {
        userName: null,        
        name: null,
        email: null,       
        userMail: null,
        telefone: null,
        userPhone: null,        
        userAccept: null,

        result: {
          name: this.result, 
          telefone: this.result2
        }
       
      }
    
    },
    
     async created() {
       

      var userData = []
      await db.collection("users").get().then((querySnapshot) => {
      querySnapshot.forEach((doc) => {
          console.log(`${doc.id} => ${doc.data()}`);          
          userData.push(doc.data())
          
         
          
          
          
          
    });

    
});   
      


      this.user = userData.map(a => a).sort((a) => a.user)  
      


       console.log(result)
       sortedArray() 
      
      
    },
    
    
  }      
   
</script>

