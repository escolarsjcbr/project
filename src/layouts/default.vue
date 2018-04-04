<template>
  <q-layout view="hhh LpR fFf">
    <q-layout-header>
      <q-toolbar
        color="primary"
        :glossy="$q.theme === 'mat'"
        :inverted="$q.theme === 'ios'"
      >

        <q-toolbar-title class="text-center">
          Transporte Escolar
          <div slot="subtitle">São José dos Campos - SP</div>
        </q-toolbar-title>

      </q-toolbar>
    </q-layout-header>

    <q-layout-drawer
      side="right"
      v-model="rightDrawerOpen"
      :content-class="$q.theme === 'mat' ? 'bg-grey-3' : null"
    >

      <q-list
        no-border
        link
        inset-delimiter
      >

      <q-list-header>Login</q-list-header>

        <q-input v-model="text" stack-label="E-mail" class="q-ma-sm" />
        <q-input v-model="text" type="password" stack-label="Senha" class="q-ma-sm" />

        <q-btn icon="account_circle" color="primary" label="entrar" class="q-ma-sm" />
      </q-list>

    </q-layout-drawer>

    <q-layout-drawer
      v-model="leftDrawerOpen"
      :content-class="$q.theme === 'mat' ? 'bg-grey-3' : null"
    >

      <q-list
        no-border
        link
        inset-delimiter
      >

      <q-list-header>Procurar motoristas</q-list-header>
        <q-field
          label="Escola:"
          helper="exemplo: antônio palmas"
          error-label="Informe a escola"
          :count="40"
          class="q-ma-sm"
        >
          <q-input v-model="escola.nome" />
        </q-field>

        <q-radio v-model="option" val="opt1" label="Particular" class="q-ma-sm" />
        <q-radio v-model="option" val="opt2" label="Prefeitura" class="q-ma-sm" />

        <q-btn icon="search" color="primary" label="procurar" class="q-ma-sm" />
      </q-list>

    </q-layout-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <!-- optional -->
    <q-layout-footer>
      <!-- content; any -->
      <q-toolbar
        color="primary"
      >
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Search"
        >
          <q-icon name="search" />
        </q-btn>

        <q-toolbar-title>

        </q-toolbar-title>

        <q-btn
          flat
          dense
          round
          @click="rightDrawerOpen = !rightDrawerOpen"
          aria-label="Login"
        >
          <q-icon name="account_circle" />
        </q-btn>
      </q-toolbar>
    </q-layout-footer>
  </q-layout>
</template>

<script>
import { openURL } from 'quasar'

export default {
  name: 'LayoutDefault',
  data () {
    return {
      leftDrawerOpen: this.$q.platform.is.desktop,
      rightDrawerOpen: false,
      option: 'opt1',
      text: '',
      escola: {
        nome: ''
      }
    }
  },
  methods: {
    openURL
  }
}
</script>

<style>
</style>
