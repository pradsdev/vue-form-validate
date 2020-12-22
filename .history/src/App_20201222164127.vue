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
      <Form @details="recentlySubmittedData"/>
      <Table/>
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
  
  }),
  methods: {
    recentlySubmittedData (data) {
      console.log(data)
    }
  }
}
</script>
