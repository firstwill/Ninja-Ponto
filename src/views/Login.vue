<template>
    <div>
      <v-card>
      <v-tabs dark background-color="primary lighten-1" show-arrows>
       <v-col class="primary lighten-1 py-3 text-center white--text" cols="13">    
      <v-toolbar-title >NINJA PONTO</v-toolbar-title>
      </v-col> 
      </v-tabs>
    </v-card>  
       <v-app id='inspire'> 
        <v-row align="center" justify="center" >          
          <v-layout align="center" justify-center>          
          <v-flex xs12 sm8 md4 >          
            <v-card class="elevation-20">
              <v-toolbar color="primary" dark flat>
                <v-toolbar-title>Fazer Login</v-toolbar-title> 
              </v-toolbar>
              <v-card-text>
                <v-form>
                  <v-text-field label="Usuario" name="Login"  type="text"></v-text-field>
                  <v-text-field id="password" label="Senha" name="password"  type="password">
                  </v-text-field>
                </v-form>
              </v-card-text>
              <v-card-actions>
               <v-btn router-link :to="{name:'cadastro'}" color="primary">
               Cadastro</v-btn>
                <v-spacer></v-spacer>
                <v-btn router-link :to="{name:'home'}" color="primary">
                Login</v-btn>
              </v-card-actions>
            </v-card>           
          </v-flex>           
        </v-layout>        
        </v-row>
      </v-app>        
      <v-row>
        <v-btn
          v-for="link in links" :key="link" color="white" text rounded class="my-2">
          {{ link }}
        </v-btn>
        <v-col class="primary lighten-1 py-4 text-center white--text" cols="12">
        </v-col>
      </v-row>   
    </div>
</template>



<script>
export default {
  data () {
    return {
      show1: false,
      show2: true,
      show3: false,
      show4: false,
      password: 'Password',
      rules: {
        required: value => !!value || 'Required.',
        min: v => v.length >= 8 || 'Min 8 characters',
        emailMatch: () => ('The email and password you entered don\'t match'),
      },
    }
  },
}
</script>