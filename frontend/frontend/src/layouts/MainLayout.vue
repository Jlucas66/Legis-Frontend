<template>
  <q-layout view="lHh Lpr lFf" >
    <q-header elevated class="bg-black text-white">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-img 
          src="~assets/logoCpT.png"
          width="80px"
          height="80px"
          class="q-mr-sm"
          fit="contain"> 

        </q-img>

        <q-toolbar-title>
          LEGIS-PCPE <br/>
          Polícia Civil de Pernambuco
        </q-toolbar-title>

      
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
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

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Normas',
    caption: 'Administração',
    icon: 'code',
    link: '/TelaAdmin'
  },
  {
    title: 'Órgãos',
    caption: 'Padronização',
    icon: 'chat',
    link: '/TelaOrgaos'
  },
  {
    title: 'Tipo de Documento',
    caption: '',
    icon: 'drive_file_move',
    link: '/TelaTipoDocumento'
  },
  {
    title: 'Sair',
    caption: '',
    icon: 'exit_to_app',
    link: '/'
  }
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
