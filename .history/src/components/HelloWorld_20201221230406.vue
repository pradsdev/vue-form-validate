<template>
  <v-container fill-height>
    <v-row class="text-center justify-center">
      <v-col cols="6">
        <v-card>
          <v-card-title class="py-5 mx-2">
            Register Yourself to get exciting gifts
          </v-card-title>
          <v-form class="mx-6 py-8">
              <v-text-field outlined label="Full Name"/>
              <v-text-field outlined label="Email"/>
          </v-form>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',

  data: () => ({
  })
}
</script>
