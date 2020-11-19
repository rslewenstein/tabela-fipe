<template>
  <v-app>
    <v-app-bar
      app
      color="gray"
     
    >
     <div class="app-title">
        Tabela Fipe
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