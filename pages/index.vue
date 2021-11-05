<template>
  <v-container class="mt-6">
    <v-row>
      <v-col class="d-flex justify-center">
        <v-card :width="'90%'">
          <v-card-title>
            <h3 class="text-center text-uppercase">Formulário VAS</h3>
          </v-card-title>
          <v-card-text>
            <v-row>
              <v-col>
                <v-form id="vas-form" ref="vasForm" v-model="vasFormStatus">
                  <v-row>
                    <v-col cols="12">
                      <v-text-field
                        v-model="name"
                        dense
                        clearable
                        label="Nome Completo"
                        outlined
                        placeholder="Digite seu nome completo!"
                        :rules="[rules.required]"
                      >
                      </v-text-field>
                    </v-col>
                    <v-col cols="12">
                      <v-row class="mb-3">
                        <v-col cols="6">
                          <span>Sem Dor</span>
                        </v-col>
                        <v-col class="d-flex justify-end" cols="6">
                          <span>Dor insuportável</span>
                        </v-col>
                      </v-row>
                      <v-row>
                        <v-col class="px-6">
                          <v-slider
                            v-model="value"
                            class="mx-auto"
                            color="blue"
                            :max="10"
                            :min="0"
                            :step="0.01"
                            :thumb-color="'blue darken-3'"
                            :thumb-label="'always'"
                            :prepend-icon="'0'"
                            :append-icon="'10'"
                          ></v-slider>
                        </v-col>
                      </v-row>
                    </v-col>
                  </v-row>
                  <v-row>
                    <v-col>
                      <v-btn
                        block
                        large
                        color="blue"
                        :dark="vasFormStatus"
                        :disabled="!vasFormStatus"
                        @click="sendEmail"
                      >
                        <span>Enviar</span>
                      </v-btn>
                    </v-col>
                  </v-row>
                </v-form>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
const INPUT_REQUIRED = (value) => !!value || 'Campo obrigatório.'
export default {
  name: 'CreditoFacil',
  data: () => ({
    rules: {
      required: INPUT_REQUIRED,
    },
    name: null,
    value: 5,
    vasFormStatus: false,
  }),

  methods: {
    sendEmail() {
      const email = 'clinicagap.fo@usp.br'
      const subject = 'Resultado VAS'
      const emailBody = `Nome: ${this.name} / Nota: ${this.value}`
      document.location =
        'mailto:' + email + '?subject=' + subject + '&body=' + emailBody
    },
  },
}
</script>

