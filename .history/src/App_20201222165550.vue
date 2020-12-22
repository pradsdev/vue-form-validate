<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <div class="title">
          Pradsdev
        </div>
      </div>
    </v-app-bar>

    <v-main>
      <v-container fill-height>
        <v-row class="text-center justify-center">
          <Form @update="($event) => items.push($event)"/>
          <Table v-if="items.length > 0":data="items"/>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  components: {
    Form: () => import('./components/Form'),
    Table: () => import('./components/Table')
  },

  data: () => ({
    items: []
  })
}
</script>
