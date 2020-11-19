<template>
    <div class="main">
    <h1>Tabela Fipe</h1>

    <!-- <v-select 
            v-model="select"
            :items="veiculos"
            label="Veículo"
        ></v-select> -->

    <!-- <v-btn
      class="button"
      small
      color="primary"
      dark
    >
        Checar
    </v-btn> -->

    <v-simple-table class="table">
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">
            Nome
          </th>
          <th class="text-left">
            Código
          </th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="item in list" 
          v-bind:key="item.id"
        >
          <td>{{ item.nome }}</td>
          <td>{{ item.codigo }}</td>
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
        return {list:undefined}
    },
    mounted(){
        Vue.axios.get('https://parallelum.com.br/fipe/api/v1/carros/marcas')
        .then((resp) => {
            this.list=resp.data;
            // console.warn(resp.data)
        })
    }
}
</script>

<style scoped>
h1{
    text-align: center;
}

.table{
    max-width: 600px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    margin-left: 30%;
    margin-top: 5%;
    padding: 10px;
}
.button{
  text-align: center;
}
</style>