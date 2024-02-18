<template>
    <q-page>

        <div class="page-container row">


            <q-card class="col-12 text-center text-h4" bordered flat>
                <q-card-section>
                    <q-item-label>
                        Matriculas
                    </q-item-label>
                </q-card-section>
            </q-card>



            <div class="col-12">

            <q-card class="q-ma-md q-pa-md" bordered flat>

                <q-tabs v-model="tab" dense class="text-grey" active-color="primary" indicator-color="primary"
                    align="left" narrow-indicator>
                    <q-tab name="ativo" label="Ativo" />
                    <q-tab name="inativo" label="Inativo" />
                </q-tabs>

            </q-card>
        </div>


        

        </div>

        <div class="q-pa-md">
                <q-table
                class="my-sticky-header-table"
                flat bordered
                :rows="rows"
                :columns="columns"
                row-key="name"
                >
                </q-table>
        </div>

        <q-dialog v-model="addButton" persistent>
            <q-card style="width:700px">
                <q-card-section>
                <div class="text-h6">Novo Curso</div>
                </q-card-section>

                <q-card-section class="q-pt-none">

                    <q-select class="q-my-sm" outlined label="Àrea de Formação" :options="[
                        'METROLOGIA',
                        'ELECTRICIDADE, ENERGIAS RENOVÁVEIS E MECATRÔNICA',
                        'TECNOLÓGIA DE INFORMAÇÃO E COMUNICAÇÃO',
                        'MECÂNICA E PRODUÇÃO'
                    ]" ></q-select>

                    <q-input class="q-my-sm" outlined v-model="text" label="Nome" />
                    <q-input class="q-my-sm" outlined v-model="text" label="Carga horária" type="number" />
                    <q-input class="q-my-sm" outlined v-model="text" label="Inicio" type="date" />
                    <q-input class="q-my-sm" outlined v-model="text" label="Término" type="date" />
                    <q-select class="q-my-sm" outlined label="Turno" :options="[
                        'Manhã',
                        'Tarde',
                        'Noite'
                    ]" ></q-select>
                    
                       <q-input class="q-my-sm" outlined v-model="text" label="Preço" prefix="AOA" />



                </q-card-section>

                <q-card-actions align="right">
                    <q-btn flat label="Salvar" color="primary" v-close-popup />
                    <q-btn flat label="Cancelar" color="primary" v-close-popup />
                </q-card-actions>
            </q-card>
         </q-dialog>

    </q-page>
</template>
  
<script>
import { defineComponent, ref } from 'vue'

export default {
  setup () {
    return {
      tab: ref('ativo'),
      addButton: ref(false)
    }
  }
}


</script>
  