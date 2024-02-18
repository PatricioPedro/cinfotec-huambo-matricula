<template>
  <q-layout view="lHh Lpr lFf">
    <q-header  class="primary-color">
      <q-toolbar>
       
          <q-space/>
          <q-btn icon="logout" round flat ></q-btn>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      class="primary-color"
    >
      <q-list>
        <q-item-label
          header
          class="text-white text-h5"
        >
          Cinfotec Huambo
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

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
