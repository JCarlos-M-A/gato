<template>
  <div>
    <v-alert v-model="alerta" border="top" type="success" dark>
      Gana jugador {{ valor }}
    </v-alert>
  </div>
</template>

<script>
export default {
  props: {
    valor: {
      type: String,
    },
    mostrar: {
      type: Boolean,
    },
  },
  data: () => ({
    //
    alerta: false,
  }),
  watch: {
    // whenever question changes, this function will run
    mostrar(value) {
      this.alerta = value;
    },
  },
};
</script>