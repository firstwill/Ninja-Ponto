<template>
  <div class="home">
    <v-app id="inspire" color="grey darken-4">
    <v-navigation-drawer
      v-model="drawer" app clipped>
      <v-list dense>
        <v-list-item  @click="navigateTo('registros')">
          <v-list-item-action >
            <v-icon color="grey darken-4">Registros</v-icon>
          </v-list-item-action>
          <v-list-item-content>
          </v-list-item-content>
        </v-list-item>
        <v-list-item  @click="navigateTo('usuarios')">
          <v-list-item-action >
            <v-icon color="grey darken-4">Usuarios</v-icon>
          </v-list-item-action>
          <v-list-item-content>
          </v-list-item-content>
        </v-list-item>
        <v-list-item @click="navigateTo('login')">
          <v-list-item-action>
            <v-icon color="grey darken-4">Sair</v-icon>
          </v-list-item-action>
          <v-list-item-content>
          </v-list-item-content>
        </v-list-item>    
      </v-list>
    </v-navigation-drawer>
    <v-app-bar color="primary lighten-1" app clipped-left> 
    <v-app-bar-nav-icon color="grey lighten-5" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
    <v-switch v-model="$vuetify.theme.dark" hide-details inset label="Tema"></v-switch>
    <v-col class="primary lighten-1 py-3 text-center white--text" cols="13">  
    <v-toolbar-title>NINJA PONTO</v-toolbar-title>
    </v-col>
    </v-app-bar>
      <v-row justify="center">
        </v-btn-toggle>
      </v-row>
      <v-time-picker
        v-model="picker"
        class="mt-2"
        :disabled="disabled"
        :readonly="readonly"
        :landscape="landscape"
        :ampm-in-title="ampmInTitle"
        :use-seconds="useSeconds"
        :format="format"
        :full-width="fullWidth"
        :no-title="noTitle"
        :scrollable="scrollable"
      ></v-time-picker>
    </v-row>
    <v-row align="center" justify="center">
      <v-col class="text-center" cols="30" sm="5">
        <div class="my-12">
          <v-btn large color="primary">Registrar Ponto</v-btn>
        </div>
      </v-col>
    </v-row>
    <v-content>
      <v-container fluid fill-height>
        <v-layout align-center justify-center>
          <v-flex shrink>
            <v-tooltip right>
            </v-tooltip> 
            <router-view/>
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
    <v-col class="primary lighten-1 py-4 text-center white--text" cols="13"></v-col>
  </div>
</template>




<script>
export default {
  data: () => ({
    drawer: false,

      return:{
      picker: null,
      disabled: false,
      readonly: false,
      landscape: false,
      ampmInTitle: false,
      useSeconds: false,
      format: 'ampm',
      fullWidth: false,
      noTitle: false,
      scrollable: false,
    }
  }),
  methods: {
    navigateTo(where){
      this.$router.push({name: where})
    }
  },   
}
</script>