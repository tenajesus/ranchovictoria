<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Rancho Victoria </q-toolbar-title>

        
      </q-toolbar>
      <div class="q-px-lg q-mb-md">
        <div class="text-subtitle1">
          {{ fecha }}
        </div>
      </div>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list padding>
        
        <q-item-label header> Menú Principal </q-item-label>
    
          <q-item clickable v-ripple to="/">
            <q-item-section avatar>
              <q-icon name="home" />
            </q-item-section>

            <q-item-section> Home </q-item-section>
          </q-item>

          <q-item clickable v-ripple to="/registro">
            <q-item-section avatar>
              <q-icon name="add" />
            </q-item-section>
            <q-item-section> Registro Animal </q-item-section>
          </q-item>

          <q-item clickable v-ripple to="/seguimiento">
            <q-item-section avatar>
              <q-icon name="analytics" />
            </q-item-section>
            <q-item-section> Seguimiento de Pesaje </q-item-section>
          </q-item>

          <q-item clickable v-ripple to="/vacunas">
            <q-item-section avatar>
              <q-icon name="vaccines" />
            </q-item-section>
            <q-item-section> Vacunación </q-item-section>
          </q-item>

        <q-item clickable v-ripple to="/ventas">
            <q-item-section avatar>
              <q-icon name="paid" />
            </q-item-section>
            <q-item-section> Ventas </q-item-section>
          </q-item>

        <q-item clickable v-ripple to="/expediente">
            <q-item-section avatar>
              <q-icon name="folder" />
            </q-item-section>
            <q-item-section> Expediente animal </q-item-section>
          </q-item>
          
          <q-item clickable v-ripple to="/salir">
            <q-item-section avatar>
              <q-icon name="logout" />
            </q-item-section>
            <q-item-section> Cerrar sesión </q-item-section>
          </q-item>

        <EssentialLink
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
    <q-footer elevated>
      <q-toolbar class="glossy">
        <q-toolbar-title class="text-caption">
          Universidad Autónoma de Zacatecas - Maestría en ciencias del procesamiento
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";

const linksList = [

  
];

import { defineComponent, ref } from "vue";
import { date } from "quasar";

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
  computed: {
    fecha() {
      const timeStamp = Date.now();
      return (date.formattedString = date.formatDate(timeStamp, "DD-MM-YYYY"));
    },
  }
});
</script>
