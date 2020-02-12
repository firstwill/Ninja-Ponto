<template>

     <div>
     <v-card>
      <v-tabs dark background-color="primary lighten-1" show-arrows>
      <v-btn router-link :to="{name:'login'}" large color="primary">Sair</v-btn>
       <v-col class="primary lighten-1 py-3 text-center white--text" cols="13">    
       <v-toolbar-title >NINJA PONTO</v-toolbar-title>
      </v-col> 
      </v-tabs>
    </v-card>  
       <v-app id="inspire">
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="6">
        <v-card ref="form">
          <v-card-text>
            <v-text-field
              ref="name"
              v-model="name"
              :rules="[() => !!name || 'Este campo é obrigatório']"
              :error-messages="errorMessages"
              label="Nome Completo"
              placeholder="Ex: João Siqueira"
              required
            ></v-text-field>
            <v-text-field
              ref="address"
              v-model="address"
              :rules="[
                () => !!address || 'Este campo é obrigatório',
                () => !!address && address.length <= 25 || 'Address must be less than 25 characters',
                addressCheck
              ]"
              label="Endereço"
              placeholder="Ex: rua Mariana 220"
              counter="25"
              required
            ></v-text-field>
            <v-text-field
              ref="city"
              v-model="Cidade"
              :rules="[() => !!city || 'Este campo é obrigatório', addressCheck]"
              label="Cidade"
              placeholder="Ex: Campinas"
              required
            ></v-text-field>
            <v-text-field
              ref="state"
              v-model="state"
              :rules="[() => !!state || 'Este campo é obrigatório']"
              label="Estado / Província / Região"
              required
              placeholder="Ex: SP"
            ></v-text-field>
            <v-text-field
              ref="zip"
              v-model="zip"
              :rules="[() => !!zip || 'Este campo é obrigatório']"
              label="CEP / Código Postal"
              required
              placeholder="79938"
            ></v-text-field>
            <v-content>      
        <v-layout align-center justify-center>
          <v-flex >
            <v-card >
              <v-spacer></v-spacer> 
              <v-card-text>
                <v-form>
                  <v-text-field label="Usuario" name="Login"  type="text"></v-text-field>

                  <v-text-field id="password" label="Senha" name="password"  type="password">
                  </v-text-field>
                  <v-text-field id="password" label="Confirmar Senha" name="password"  type="password">
                  </v-text-field>
                </v-form>
              </v-card-text>              
            </v-card>
          </v-flex>
        </v-layout>     
    </v-content>
          </v-card-text>
          <v-divider class="mt-12"></v-divider>
          <v-card-actions>
            <v-btn router-link :to="{name:'login'}" text>Cancelar</v-btn>
            <v-spacer></v-spacer>
            <v-slide-x-reverse-transition>
              <v-tooltip
                v-if="formHasErrors"
                left>
                <template v-slot:activator="{ on }">
                  <v-btn
                    icon
                    class="my-0"
                    @click="resetForm"
                    v-on="on">
                    <v-icon>mdi-refresh</v-icon>
                  </v-btn>
                </template>
                <span>Refresh form</span>
              </v-tooltip>
            </v-slide-x-reverse-transition>
            <v-btn  color="primary" text @click="submit">Concluir</v-btn>
          </v-card-actions>
          
        </v-card>
      </v-col>
      </v-row>
  </v-app>
  <v-card>
      <v-tabs dark background-color="primary lighten-1" show-arrows>
       <v-col class="primary lighten-1 py-4 text-center white--text" cols="13">    
     
      </v-col> 
      </v-tabs>
    </v-card>  
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