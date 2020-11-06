<template>  
    <v-form class="form1">
        <v-spacer></v-spacer>
        <v-icon>
            mdi-account
        </v-icon>
        Email:
        <v-text-field id='login1' type="email" v-model="email" style="width:400px">

        </v-text-field>
        <v-icon>
            mdi-key
        </v-icon>
        Senha:
        <v-text-field id='pass1' type="password" v-model="password" style="width:400px"> </v-text-field>
        <v-btn @click="login" color="primary">Entrar</v-btn>
    </v-form>
</template>

<script>
import firebase from 'firebase'
import router from '../router'


export default {
    name: 'App',
    components: {
        //
    },
    data() {
        return {
            email: "",
            password: ""
        }
    },
    methods: {
        login: function () {
            firebase.auth().signInWithEmailAndPassword(this.email, this.password).then(
                user => {
                    router.push('/home');
                },
                err => {
                    alert(err)
                }
            )
        }
    }
}
</script>

<style scoped>

.form1 {
  width: 400px;
  position: absolute;
  margin-left: 33%;
  margin-top: 10%;
  background-color: rgba(255, 255, 255, 0.685);
  text-align: center;
  
}



</style>