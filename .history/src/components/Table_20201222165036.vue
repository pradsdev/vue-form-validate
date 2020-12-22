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
