<template>
  <v-app>
    <AppBar />
    <v-main>
      <div class="d-flex justify-center ma-4">{{ turno }}</div>
      <div class="d-flex justify-center align-center">
        <div class="d-flex flex-wrap" style="width: 250px">
          <v-btn
            v-for="boton in botones"
            :key="boton.id"
            outlined
            color="indigo"
            class="ma-2"
            @click="tira(boton)"
          >
            {{ boton.texto }}
          </v-btn>
        </div>
      </div>
      <div>
        <v-btn color="indigo" class="ma-2" outlined @click="reiniciar">
          Reiniciar
        </v-btn>
      </div>
    </v-main>

    <Alert :valor="alertaText" :mostrar="mostrar" :tipo="tipo" />
  </v-app>
</template>

<script>
import AppBar from "./components/AppBar.vue";
import Alert from "./components/Alert.vue";

export default {
  name: "App",

  components: {
    //
    AppBar,
    Alert,
  },

  data: () => ({
    //
    turno: "X",
    alertaText: "",
    mostrar: false,
    turnos: 0,
    tipo: "success",
    botones: [
      {
        id: 1,
        texto: "",
      },
      {
        id: 2,
        texto: "",
      },
      {
        id: 3,
        texto: "",
      },
      {
        id: 4,
        texto: "",
      },
      {
        id: 5,
        texto: "",
      },
      {
        id: 6,
        texto: "",
      },
      {
        id: 7,
        texto: "",
      },
      {
        id: 8,
        texto: "",
      },
      {
        id: 9,
        texto: "",
      },
    ],
  }),
  methods: {
    reiniciar() {
      this.botones = [
        {
          id: 1,
          texto: "",
        },
        {
          id: 2,
          texto: "",
        },
        {
          id: 3,
          texto: "",
        },
        {
          id: 4,
          texto: "",
        },
        {
          id: 5,
          texto: "",
        },
        {
          id: 6,
          texto: "",
        },
        {
          id: 7,
          texto: "",
        },
        {
          id: 8,
          texto: "",
        },
        {
          id: 9,
          texto: "",
        },
      ];
      this.turnos = 0;
    },
    tira(boton) {
      if (boton.texto == "") {
        boton.texto = this.turno;
        this.checkWin(this.turno);
        if (this.turno == "X") {
          this.turno = "O";
        } else {
          this.turno = "X";
        }
      } else {
        this.mostrar = true;
        this.alertaText = "-_-";
        this.tipo = "info";
        setTimeout(() => {
          this.mostrar = false;
        }, 2500);
      }
    },
    win(jugador) {
      if (jugador != "empate") {
        this.mostrar = true;
        this.alertaText = "Gana jugador " + jugador;
        setTimeout(() => {
          this.mostrar = false;
        }, 2500);
      } else {
        if (this.turnos == 9) {
          this.mostrar = true;
          this.alertaText = "Empate";
          this.tipo = "info";
          setTimeout(() => {
            this.mostrar = false;
          }, 2500);
        }
      }
    },
    checkWin(variale) {
      if (
        this.botones[0].texto == variale &&
        this.botones[1].texto == variale &&
        this.botones[2].texto == variale
      ) {
        this.win(variale);
      } else {
        if (
          this.botones[3].texto == variale &&
          this.botones[4].texto == variale &&
          this.botones[5].texto == variale
        ) {
          this.win(variale);
        } else {
          if (
            this.botones[6].texto == variale &&
            this.botones[7].texto == variale &&
            this.botones[8].texto == variale
          ) {
            this.win(variale);
          } else {
            if (
              this.botones[0].texto == variale &&
              this.botones[3].texto == variale &&
              this.botones[6].texto == variale
            ) {
              this.win(variale);
            } else {
              if (
                this.botones[1].texto == variale &&
                this.botones[4].texto == variale &&
                this.botones[7].texto == variale
              ) {
                this.win(variale);
              } else {
                if (
                  this.botones[3].texto == variale &&
                  this.botones[5].texto == variale &&
                  this.botones[8].texto == variale
                ) {
                  this.win(variale);
                } else {
                  if (
                    this.botones[0].texto == variale &&
                    this.botones[4].texto == variale &&
                    this.botones[8].texto == variale
                  ) {
                    this.win(variale);
                  } else {
                    if (
                      this.botones[2].texto == variale &&
                      this.botones[4].texto == variale &&
                      this.botones[6].texto == variale
                    ) {
                      this.win(variale);
                    } else {
                      this.turnos++;
                      this.win("empate");
                    }
                  }
                }
              }
            }
          }
        }
      }
    },
  },
};
</script>
