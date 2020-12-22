<template>
  <v-container fill-height>
    <v-row class="text-center justify-center">
      <v-col cols="5">
        <v-card>
          <v-card-title class="py-8 display-1 mx-2 d-flex flex-row justify-center">
            <div>
              Register Now
            </div>
          </v-card-title>
          <v-form
            ref="form"
            class="mx-6"
            @submit.prevent="submitForm"
          >
            <v-text-field
              v-model="name"
              outlined
              label="Full Name"
              :rules="[v => !!v || 'Full Name is required', v => /^[a-zA-Z]+(?:[\s.]+[a-zA-Z]+)*$/.test(v) || 'Full name must be valid']"
              prepend-icon="mdi-account"
            />
            <v-text-field
              v-model="email"
              outlined
              label="Email"
              :rules="[v => !!v || 'Email is required', v => /^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,63})+$/.test(v) || 'Email must be valid']"
              prepend-icon="mdi-email"
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
                  :rules="[v => !!v || 'Age is required']"
                  v-bind="attrs"
                  v-on="on"
                />
              </template>
              <v-date-picker
                ref="picker"
                v-model="date"
                :max="ageLimitDate"
                @change="save"
              />
            </v-menu>
            <v-select
              v-model="region"
              :items="items"
              label="Region"
              outlined
              :rules="[v => !!v || 'Region is required']"
              prepend-icon="mdi-map"
            />
            <v-checkbox
              v-model="checkbox"
              :rules="[v => !!v || 'Please check the checkbox']"
              label="I Agree to Terms and Conditions"
            />
          </v-form>
          <v-card-actions class="px-6 pb-4">
            <v-spacer></v-spacer>
            <v-btn
              :loading="loading"
              color="primary"
              type="submit"
              depressed
              @click="submitForm"
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
import axios from 'axios'
import * as moment from 'moment'
export default {
  name: 'HelloWorld',
  data: () => ({
    date: null,
    menu: false,
    items: ['Africa', 'Americas', 'Asia', 'Europe', 'Oceania'],
    checkbox: false,
    loading: false,
    region: '',
    name: '',
    email: '',
    ageLimitDate: ''
  }),
  mounted () {
    const ageLimitDate = moment().subtract(18, 'years').format('YYYY-MM-DD')
    this.ageLimitDate = ageLimitDate
  },
  watch: {
    menu (val) {
      val && setTimeout(() => (this.$refs.picker.activePicker = 'YEAR'))
    }
  },
  methods: {
    save (date) {
      this.$refs.menu.save(date)
    },
    async submitForm () {
      if (!this.$refs.form.validate()) return
      this.loading = true
      const data = {
        name: this.name,
        email: this.email,
        age: moment().diff(this.date, 'years', false),
        region: this.region
      }
      const result = await axios.get(`https://restcountries.eu/rest/v2/region/${this.region}`)
      this.loading = false
      console.log(result, data)
    }
  }
}
</script>
