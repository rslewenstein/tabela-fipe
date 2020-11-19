<template>
  <v-app>
    <v-app-bar
      app
      color="gray"
     
    >
     <div class="app-title">
        <v-text>Tabela Fipe</v-text>
      </div>


      <v-spacer></v-spacer>

    </v-app-bar>

    <v-main>
      <TabelaFipe/>
    </v-main>
  </v-app>
</template>

<script>
import TabelaFipe from './components/TabelaFipe';

export default {
  name: 'App',

  components: {
    TabelaFipe,
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>
.app-title{
  font-size: 40px;
  font-family: fantasy;
}
</style>