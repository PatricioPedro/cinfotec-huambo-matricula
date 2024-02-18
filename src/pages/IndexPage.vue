<template>
  <q-page class="cinfotec-page">

    <!-- <div class="page-container row">

      <q-card class="col-12 text-center text-h4" bordered flat>
        <q-card-section>
          <q-item-label>
            Formulário Online de Pré-Inscrição
          </q-item-label>
        </q-card-section>
      </q-card>

    </div> -->


    <fieldset>
      <legend>Dados do Curso
        <q-btn no-caps label="Escolher curso" @click="addButton = true" flat color="primary" />

      </legend>
      <q-card-section class="q-pt-none">

        <q-input class="q-my-sm" outlined dense v-model="text" label="Nome do Curso" readonly />
        <q-input class="q-my-sm" outlined dense v-model="text" label="Turma" readonly />
        <q-input class="q-my-sm" outlined dense v-model="text" label="Turno" readonly />

      </q-card-section>
    </fieldset>
    <fieldset>
      <legend>Dados pessoais </legend>
      <q-card-section class="q-pt-none">

        <q-file label="Foto" outlined dense v-model="model">
          <template v-slot:prepend>
            <q-icon name="attach_file" />
          </template>
        </q-file>

        <fieldset>
          <legend>Dados do Bilhete de Identidade</legend>

          <div class="row justify-between q-gutter-y-sm">
            <div class="col-5">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Número" />

            </div>
            <div class="col-3">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Emissão" type="date" />

            </div>
            <div class="col-3">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Validade" type="date" />

            </div>

            <div class="col-6 q-mx-sm">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Data de Nascimento" type="date" />

            </div>

            <div class="col-5 q-mx-sm">
              <q-select class="q-my-sm" :options="['Solteiro', 'Casado']" outlined dense v-model="text" label="Estado Cívil"
                type="date" />

            </div>

            <div class="col-6 q-mx-sm">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Naturalidade" />
            </div>


            <div class="col-5 q-mx-sm">
              <q-select class="q-my-sm" :options="['Huambo', 'Luanda']" outlined dense v-model="text" label="Província"
                type="date" />
            </div>


            <div class="col-6 q-mx-sm">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Nome do Pai" />

            </div>

            <div class="col-5 q-mx-sm">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Nome da Mãe" />
            </div>

            <div class="col-6 q-mx-sm">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Residência" />
            </div>

            <div class="col-5 q-mx-sm">
              <q-input class="q-my-sm" outlined dense v-model="text" label="Município" />
            </div>

            <div class="col-6 q-mx-sm">
              <q-file label="Anexo B.I" outlined dense v-model="model">
                <template v-slot:prepend>
                  <q-icon name="attach_file" />
                </template>
              </q-file>
            </div>

            <div class="col-5 q-mx-sm">
             <div class="row">
              Sexo:
             </div>

              <q-radio dense v-model="shape" val="line" label="Masculino" />
              <q-radio dense v-model="shape" val="rectangle" label="Feminino" />
            </div>

         


          </div>

          
        </fieldset>

        <div class="row justify-between">
          <div class="col-6">
            <q-input class="q-my-sm" outlined dense v-model="text" label="Telefone" />
          </div>
          <div class="col-5">
            <q-input class="q-my-sm" outlined dense v-model="text" label="E-mail" />
          </div>
          <div class="col-6">
            <q-input class="q-my-sm" outlined dense v-model="text" label="Profissão" />
          </div>
          <div class="col-5">
            <q-input class="q-my-sm" outlined dense v-model="text" label="Morada atual" />
          </div>

        </div>

      </q-card-section>
    </fieldset>

    <fieldset>

      <legend>
        Formação Escolar
      </legend>

      <div class="column">
        <q-radio dense v-model="shape" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="line"
          label="Ensino Médio" />
        <q-radio dense v-model="shape" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="rectangle"
          label="Ensino Superior Incompleto" />
        <q-radio dense v-model="shape" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="ellipse"
          label="Ensino Superior" />
        <q-radio dense v-model="shape" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="polygon"
          label="Pós-graduação" />
        <q-radio dense v-model="shape" checked-icon="task_alt" unchecked-icon="panorama_fish_eye" val="polygon"
          label="Outras formações / Cursos" />
      </div>
    </fieldset>


    <fieldset>
      <legend>Dados da Empresa</legend>
      <div class="row justify-between">
        <div class="col-6">
          <q-input class="q-my-sm" outlined dense v-model="text" label="Nome" />
        </div>
        <div class="col-5">
          <q-input class="q-my-sm" outlined dense v-model="text" label="Endereço" />
        </div>
        <div class="col-6">
          <q-input class="q-my-sm" outlined dense v-model="text" label="Município" />
        </div>
        <div class="col-5">
          <q-input class="q-my-sm" outlined dense v-model="text" label="Província" />
        </div>
        <div class="col-6">
          <q-input class="q-my-sm" outlined dense v-model="text" label="Telefone" />
        </div>

      </div>

    </fieldset>



    <q-card-actions align="right" class="row justify-center">
      <q-btn square  label="Enviar Inscrição" class="col-6 primary-color text-white" v-close-popup />
    </q-card-actions>

    <q-dialog dense v-model="addButton" persistent>
      <q-card class="col-6" style="width: 900px; max-width: 80vw;">
        <q-card-section>
          <q-select class="q-my-sm" dense outlined label="Àrea de Formação" :options="[
            'METROLOGIA',
            'ELECTRICIDADE, ENERGIAS RENOVÁVEIS E MECATRÔNICA',
            'TECNOLÓGIA DE INFORMAÇÃO E COMUNICAÇÃO',
            'MECÂNICA E PRODUÇÃO'
          ]"></q-select>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-card class="text-white text-bold" flat bordered
            style="width:70%; height: 45px; background-color: #b5894a; border-bottom-right-radius: 15px; border-top-right-radius: 15px;">

            <q-card-section>

              <q-item-label>
                <q-icon size="20px" name="precision_manufacturing" />
                METROLOGIA

              </q-item-label>
            </q-card-section>
          </q-card>


          <q-markup-table dense flat separator="none">
            <thead>
              <tr style="background-color: #a7cf89;">
                <th>Curso</th>
                <th>Carga <br />Horária</th>
                <th>Início</th>
                <th>Término</th>
                <th>Turno</th>
                <th>Preço AKz</th>
                <th>Preço <br /> Promocional AKz</th>
              </tr>
            </thead>
            <tbody>

              <tr style="background-color: #d6dce5;">
                <td class="text-center">Higiene e Segurança no Trabalho</td>
                <td class="text-center">56</td>
                <td class="text-center">-</td>
                <td class="text-center">-</td>
                <td class="text-center">Manhã/Tarde</td>
                <td class="text-center">80.000,00</td>
                <td class="text-center">40.000,00</td>
              </tr>

              <tr>
                <td class="text-center">Primeiros Socorros</td>
                <td class="text-center">40</td>
                <td class="text-center">-</td>
                <td class="text-center">-</td>
                <td class="text-center">Tarde</td>
                <td class="text-center">80.000,00</td>
                <td class="text-center">32.000,00</td>
              </tr>

              <tr style="background-color: #d6dce5;">
                <td class="text-center">Controlo de Qualidade</td>
                <td class="text-center">24</td>
                <td class="text-center">-</td>
                <td class="text-center">-</td>
                <td class="text-center">Manhã</td>
                <td class="text-center">32.850,00</td>
                <td class="text-center">32.000,00</td>
              </tr>

              <tr>
                <td class="text-center">Gestão Metrológica na Indústria</td>
                <td class="text-center">60</td>
                <td class="text-center">-</td>
                <td class="text-center">-</td>
                <td class="text-center">Manhã/Tarde</td>
                <td class="text-center">60.000,00</td>
                <td class="text-center">30.000,00</td>
              </tr>

              <tr style="background-color: #d6dce5;">
                <td class="text-center">Metrológica</td>
                <td class="text-center">24</td>
                <td class="text-center">-</td>
                <td class="text-center">-</td>
                <td class="text-center">Manhã</td>
                <td class="text-center">32.850,00</td>
                <td class="text-center">32.000,00</td>
              </tr>


            </tbody>
          </q-markup-table>

        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Fechar" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>


  </q-page>
</template>

<style>
.q-table th {
  padding: 7px 25px;
  font-size: 13px;
  border-top: none;
  background-color: inherit;
}

.q-table thead,
.q-table td,
.q-table th {
  border-style: solid;
  border-color: white;
  border-width: 1px;
}
</style>
<script>
import { defineComponent, ref } from 'vue'

export default {
  setup() {
    return {
      tab: ref('ativo'),
      addButton: ref(false)
    }
  }
}


</script>
