<template>
  <q-layout view="lHh Lpr lFf">
    <q-header bordered  class="bg-white">
      <q-toolbar >
       
        <q-toolbar-title v-if="$q.screen.gt.xs" shrink class="row items-center no-wrap">
          <img style="width:400px; height: 100px;" src="~assets/logo-cinfotec3.jpeg">

        </q-toolbar-title>
        <q-toolbar-title>
            <q-item-label class="absolute-center text-black text-bold">
              Formulário Online de Pré-Inscrição
            </q-item-label>
        </q-toolbar-title>
         

      </q-toolbar>
    </q-header>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Cursos',
    icon: 'school',
    link: '/cursos'
  },
  {
    title: 'Matrículas',
    icon: 'article',
    link: '/matriculas'
  },
  {
    title: 'Usuários',
    icon: 'person_pin',
    link: '/users'
  },

]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
