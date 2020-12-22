<template>
<table>
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
  <tr v-for="user in userData" :key="user.email">
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
      {{ user.regionDetails}}
    </td>
  </tr>

</table>
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
