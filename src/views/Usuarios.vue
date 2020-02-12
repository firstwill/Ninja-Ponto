<template>
<div id="app">
  <v-app id="inspire">
    <v-data-table
      :headers="headers"
      :items="desserts"
      sort-by="Hora de Entrada"
      class="elevation-1"
    >
    
      <template v-slot:top>
      <v-tabs dark background-color="primary lighten-1" show-arrows>
      <v-btn router-link :to="{name:'home'}" large color="primary">Voltar</v-btn>
      
       <v-col class="primary lighten-1 py-3 text-center white--text" cols="13">    
       
       <v-toolbar-title >NINJA PONTO</v-toolbar-title>

       
      </v-col> 
      </v-tabs>
          <v-divider
            class="mx-4"
            inset
            vertical
          ></v-divider>
          <v-spacer></v-spacer>
          <v-dialog v-model="dialog" max-width="500px">
            
            <v-card>
              <v-card-title>
                <span class="headline">{{ formTitle }}</span>
              </v-card-title>
  
              <v-card-text>
                <v-container>
                  <v-row>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field v-model="editedItem.name" label="Data"></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field v-model="editedItem.calories" label="Hora de Entrada"></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                      <v-text-field v-model="editedItem.fat" label="Horario de saida"></v-text-field>
                    </v-col>
                    <v-col cols="12" sm="6" md="4">
                    </v-col>
                  </v-row>
                </v-container>
              </v-card-text>
  
              <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="blue darken-1" text @click="close">Cancelar</v-btn>
                <v-btn color="blue darken-1" text @click="save">Salvar</v-btn>
              </v-card-actions>
            </v-card>
          </v-dialog>
       <v-btn router-link :to="{name:'cadastro'}" large color="primary">Cadastrar Novo Funcionario</v-btn>
      </template>
    
      <template v-slot:item.action="{ item }">
        <v-icon
          small
          class="mr-2"
          @click="editItem(item)"
        >
          editar
        </v-icon>
        <v-icon
          small
          @click="deleteItem(item)"
        >
          deletar
        </v-icon>
      </template>
      
      <template v-slot:no-data>
        <v-btn color="primary" @click="initialize">Reset</v-btn>
      </template>
    </v-data-table>
  </v-app>
</div>
</template>



<script>
export default {
  data: () => ({
    dialog: false,
    headers: [
      {
        text: 'Nome',
        align: 'left',
        sortable: false,
        value: 'nome',
      },
      { text: 'Matricula', value: 'matricula' },
      { text: 'Setor', value: 'setor' },
      { text: 'Ações', value: 'action', sortable: false },
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      name: '',
      calories: 0,
      fat: 0,
      carbs: 0,
      protein: 0,
    },
    defaultItem: {
      name: '',
      calories: 0,
      fat: 0,
      carbs: 0,
      protein: 0,
    },
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ?'' : 'Editar Funcionario'
    },
  },

  watch: {
    dialog (val) {
      val || this.close()
    },
  },

  created () {
    this.initialize()
  },

  methods: {
    initialize () {
      this.desserts = [
        {
          nome: 'João Almeida',
          matricula: '1001',
          setor: 'Comercial',
        },
        {
          nome: 'Ana Siqueira',
          matricula: '1002',
          setor: 'Comercial',
        },
        {
          nome: 'Douglas Araujo',
          matricula: '1003',
          setor: 'Recursos Humanos',
        },
        {
          nome: 'Amariudo da Silva',
          matricula: '1004',
          setor: 'Ti',
        },
        {
          nome: 'Vanessa Alice de Matos',
          matricula: '1005',
          setor: 'Recursos Humanos',
        },
        {
          nome: 'Laura Pereira',
          matricula: '1006',
          setor: 'Ti',
        },
        {
          nome: 'Otavio Caras',
          matricula: '1007',
          setor: 'Financeiro',
        },
        {
          nome: 'Alessandra Fernandes',
          matricula: '1008',
          setor: 'Marketing',
        },
        {
          nome: 'Rosana Acordes',
          matricula: '1009',
          setor: 'Comercio Exterior',
        },
        {
          nome: 'Salete Colaço',
          matricula: '1010',
          setor: 'Contabil',
        },
      ]
    },

    editItem (item) {
      this.editedIndex = this.desserts.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem (item) {
      const index = this.desserts.indexOf(item)
      confirm('Tem certeza que deseja deletar este Historico?') && this.desserts.splice(index, 1)
    },

    close () {
      this.dialog = false
      setTimeout(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      }, 300)
    },

    save () {
      if (this.editedIndex > -1) {
        Object.assign(this.desserts[this.editedIndex], this.editedItem)
      } else {
        this.desserts.push(this.editedItem)
      }
      this.close()
    },
  },
}
</script>