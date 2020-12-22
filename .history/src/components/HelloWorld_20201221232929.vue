<template>
  <v-container fill-height>
    <v-row class="text-center justify-center">
      <v-col cols="6">
        <v-card>
          <v-card-title class="py-5 mx-2">
            Register Yourself to get exciting gifts
          </v-card-title>
          <v-form class="mx-6 pt-8">
            <v-text-field
              outlined
              label="Full Name"
              prepend-icon="mdi-calendar"
            />
            <v-text-field
              outlined
              label="Email"
              prepend-icon="mdi-calendar"
            />
            <v-menu
              ref="menu"
              v-model="menu"
              :close-on-content-click="false"
              transition="scale-transition"
              offset-y
              min-width="290px"
            >
              <template v-slot:activator="{ on, attrs }">
                <v-text-field
                  v-model="date"
                  label="Birthday date"
                  prepend-icon="mdi-calendar"
                  readonly
                  outlined
                  v-bind="attrs"
                  v-on="on"
                />
              </template>
              <v-date-picker
                ref="picker"
                v-model="date"
                :max="new Date().toISOString().substr(0, 10)"
                min="1950-01-01"
                @change="save"
              />
            </v-menu>
            <v-select
              :items="items"
              label="Region"
              outlined
              prepend-icon="mdi-calendar"
            />
            <v-checkbox
              v-model="checkbox"
              label="I Agree to Terms and Conditions"
            />
          </v-form>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              :loading="loading"
              color="primary"
              type="submit"
              depressed
              @click="submit"
            >
              submit
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: () => ({
    date: null,
    menu: false,
    items: ['Africa', 'Americas', 'Asia', 'Europe', 'Oceania'],
    checkbox: false
  }),
  watch: {
    menu (val) {
      val && setTimeout(() => (this.$refs.picker.activePicker = 'YEAR'))
    }
  },
  methods: {
    save (date) {
      this.$refs.menu.save(date)
    },
    submit () {
      console.log('sadf')
    }
  }
}
</script>
