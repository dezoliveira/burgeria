<template>
  <div class="container col-4 text-center alert alert-success" role="alert">
        {{msg}}
  </div>
</template>
<script>
export default {
  name: "Message",
  props: {
    msg: String
  }
}
</script>
<style scoped>
</style>