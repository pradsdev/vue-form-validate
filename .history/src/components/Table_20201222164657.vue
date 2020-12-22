<template>
  <p>asdfasdf</p>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true,
      default: () => []
    }
  },
  data: () => ({
    userData: []
  }),
  watch: {
    items: {
      handler (val) {
        if (!val) return
        this.userData = val
      },
      immediate: true
    }
  }

}
</script>
