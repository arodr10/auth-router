<template>
  <v-app>

    <v-content>
      <v-container fluid fill-height>
        <v-slide-y-transition mode="out-in">
          <router-view/>
        </v-slide-y-transition>
      </v-container>
    </v-content>

    <messageDialog/>

    <v-footer color="primary" dark>
      <v-layout justify-center>
        <span>&copy; Copyright 2019, Monqui Technologies</span>
      </v-layout>
    </v-footer>
  </v-app>
</template>

<script>
  import MessageDialog from '@/views/MessageDialog.vue'

  export default {
    components : { MessageDialog },
    name : 'App',
    data () {
      return {
        
      }
    },
    methods : {

    }
  }
</script>