<template>
    <div>

    </div>
</template>

<script>
export default {
  name: 'Home',
  props: [
      'name', 'email', 'phone1', 'phone2', 'address1', 'address2',
      'city', 'state', 'postal_code', 'erection', 'concrete', 'grading',
      'electrical', 'plumbing', 'commercial', 'residential', 'agricultural'
  ],
  data () {
    return {
      msg: ''
    }
  }  
}
</script>

<style scoped>

</style>
