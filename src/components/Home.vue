<template>
  <div class="home">
    <div>
      {{ dealers }}
    </div>
      <create-dealer></create-dealer>
    <div>
      Form Response: {{ formResponse }}
    </div>
  </div>
</template>

<script>
import CreateDealer from './CreateDealer'
export default {
  name: 'Home',
  components: {
    CreateDealer
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      name: '',
      email: '',
      phone1: '',
      phone2: '',
      address1: '',
      address2: '',
      city: '',
      state: '',
      postal_code: '',
      dealers: [],
      formResponse: ''
    }
  },
  created () {
    this.getDealers()
  },
  methods: {
    getDealers: function () {
      this.axios.get('/api/dealers')
      .then(response => {
        this.dealers = response.data
      })
    },
    submitDealer: function () {
      this.axios({
        method: 'post',
        url: '/api/dealers',
        data: {
          name: this.name,
          email: this.email,
          phone1: this.phone1,
          phone2: this.phone2,
          address1: this.address1,
          address2: this.address2,
          city: this.city,
          state: this.state,
          postal_code: this.postal_code
        }
      }).then(response => {
        this.formResponse = response.data
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
