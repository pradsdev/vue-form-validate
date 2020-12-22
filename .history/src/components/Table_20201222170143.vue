<template>
<v-col cols="4">
  <table border="1" cellpadding="1" cellspacing="1">
  <thead>
    <td>
      Name
    </td>
    <td>
      Email
    </td>
    <td>
      Age
    </td>
    <td>
      Region
    </td>
    <td>
      Region Details
    </td>
  </thead>
  <tr v-for="user in userData" :key="user.email" valign="top">
    <td>
      {{ user.name }}
    </td>
    <td>
      {{ user.email }}
    </td>
    <td>
      {{ user.age }}
    </td>
    <td>
      {{ user.region }}
    </td>
    <td>
      {{ user.regionDetails }}
    </td>
  </tr>

</table>
</v-col>
</template>

<script>
export default {
  props: {
    data: {
      type: Array,
      required: true,
      default: () => []
    }
  },
  data: () => ({
    userData: []
  }),
  watch: {
    data: {
      handler (val) {
        if (!val) return
        this.userData = val
      },
      immediate: true
    }
  }

}
</script>
