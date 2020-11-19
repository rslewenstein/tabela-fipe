<template>
    <div class="main">
        <h1>Tabela Fipe</h1>
        <table border="1px">
            <tr>
                <td>Nome</td>
                <td>Código</td>
            </tr>
            <tr v-for="item in list" v-bind:key="item.id">
                <td>{{item.nome}}</td>
                <td>{{item.codigo}}</td>
            </tr>
        </table>
        <v-btn
            small
            color="primary"
            dark
        >
            Checar
        </v-btn>
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
            console.warn(resp.data)
        })
    }
}
</script>

<style scoped>
.main{
    text-align: center;
}
</style>