<template>
    <v-layout justify-center align-center>
        <v-flex xs12 sm8 md6 lg5 xl4>
            <v-card class="elevation-6">
                <v-toolbar color="primary" dark card>
                    <v-toolbar-title>
                    Ingresa tus Credenciales
                    </v-toolbar-title>
                </v-toolbar>
                <v-card-text>
                    <v-text-field label="Email" v-model="formulario.email"></v-text-field>
                    <v-text-field label="Password" type="Password" v-model="formulario.password"></v-text-field>            
                </v-card-text>
                <v-card-text>
                    <v-layout justify-end>
                    <v-btn color="primary" @click="ingresar">Ingresar</v-btn>
                    </v-layout>
                </v-card-text>
            </v-card>
        </v-flex>
    </v-layout>
</template>

<script>
  import { mapMutations } from 'vuex'
  import { auth_dummie, status } from '@/script/auth-firebase.js'

  export default {
    name : 'App',
    data () {
      return {
        formulario: {
          email: '',
          password: ''
        }
      }
    },
    methods : {
      ...mapMutations('notifications', ['mostrarInformacion','mostrarExito','mostrarError','mostrarOcupado','ocultarOcupado']),
      async ingresar() {
        this.mostrarOcupado({titulo : 'Validando Credenciales', mensaje : 'Estamos validando tu información...'})        
        await auth_dummie(this.formulario)
        this.ocultarOcupado()

        if (status.status_code == '0') {
          this.mostrarExito(status.status_desc)
        } else {
          this.mostrarError(status.status_desc)
        }
      }
    }
  }
</script>