<template>
  <v-container fill-height>
    <v-row class="text-center justify-center">
      <v-col cols="6">
        <v-card>
          <v-card-title>
            Form
          </v-card-title>
          <v-card-content>
            <v-form>
              <v-text-field outlined label="Full Name"/>
            </v-form>
          </v-card-content>
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
