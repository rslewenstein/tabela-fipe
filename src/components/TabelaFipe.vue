<template>
    <div class="main">
    <v-select 
      class="select-veiculos"
      v-model="select"
      :items="veiculos"
      label="Tipo Veículo"
    ></v-select>

    <v-btn
      class="button"
      small
      color="primary"
      dark
      @click="listar"
    >
        Listar
    </v-btn>

    <v-simple-table class="table">
    <template v-slot:default>
      <thead>
        <tr>
          <th class="title-table">
            Código
          </th>
          <th class="title-table">
            Fabricante
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in list" 
          v-bind:key="item.id"
          @click="listarVeiculos(select, item.codigo)"
        >
          <td>{{ item.codigo }}</td>
          <td>{{ item.nome }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
  </div>
</template>

<script>
import Vue from 'vue'
import axios from 'axios'
import VueAxios from 'vue-axios'

Vue.use(VueAxios, axios)

export default {
    data(){
        return {
          list:undefined,
          select: 'carros',
          veiculos: [
          'carros',
          'motos',
          'caminhoes'
        ]
        }
    },
    methods: {
      listar(){
        var veiculo = this.select
        Vue.axios.get('https://parallelum.com.br/fipe/api/v1/'+ veiculo +'/marcas')
        .then((resp) => {
             this.list=resp.data;
        })
      },
      listarVeiculos(veic, cod){
        console.log(veic, cod)
        Vue.axios.get('https://parallelum.com.br/fipe/api/v1/'+veic+'/marcas/'+cod+'/modelos')
        .then((resp) => {
             this.list=resp.data;
             console.log(this.list)
        })
      }
    }
    // mounted(){
    //     Vue.axios.get('https://parallelum.com.br/fipe/api/v1/caminhoes/marcas')
    //     .then((resp) => {
    //         this.list=resp.data;
    //     })
    // }
}
</script>

<style scoped>
.table{
    max-width: 600px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    margin-left: 30%;
    margin-top: 5%;
    padding: 10px;
}
.button{
  text-align: center;
  margin-left: 47%;
}
.select-veiculos{
  width: 200px;
  margin-left: 43%;
  margin-top: 2%;
}
</style>