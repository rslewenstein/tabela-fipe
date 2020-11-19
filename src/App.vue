<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        
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
