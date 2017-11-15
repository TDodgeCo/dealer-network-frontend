<template>
  <div class="create-dealer">
    <div>
      <form @submit.prevent="submitDealer">
        <div>
          <input type="text" v-model="name" placeholder="Business Name">
          <input type="text" v-model="email" placeholder="Email">
          <input type="text" v-model="phone1" placeholder="Phone Number">
          <input type="text" v-model="phone2" placeholder="Alternate Phone">
        </div>
        <div>
          <input type="text" v-model="address1" placeholder="Street Address">
          <input type="text" v-model="address2" placeholder="Street Address 2">
          <input type="text" v-model="city" placeholder="City">
          <input type="text" v-model="state" placeholder="State">
          <input type="text" v-model="postal_code" placeholder="Postal Code">
        </div>
        <div>
          <label for="erection">Erection</label>
          <input type="checkbox" @click="erection = !erection" name="erection">
          <label for="concrete">Concrete</label>
          <input type="checkbox" @click="concrete = !concrete" name="concrete">
          <label for="grading">Grading</label>
          <input type="checkbox" @click="grading = !grading" name="grading">
          <label for="electrical">Electrical</label>
          <input type="checkbox" @click="electrical = !electrical" name="electrical">
          <label for="plumbing">Plumbing</label>
          <input type="checkbox" @click="plumbing = !plumbing" name="plumbing">
          <label for="commercial">Commercial</label>
          <input type="checkbox" @click="commercial = !commercial" name="commercial">
          <label for="residential">Residential</label>
          <input type="checkbox" @click="residential = !residential" name="residential">
          <label for="agricultural">Agricultural</label>
          <input type="checkbox" @click="agricultural = !agricultural" name="agricultural">
          <input type="submit" value="Submit">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CreateDealer',
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
      erection: false,
      concrete: false,
      grading: false,
      electrical: false,
      plumbing: false,
      commercial: false,
      residential: false,
      agricultural: false,
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
          postal_code: this.postal_code,
          services: {
            erection: this.erection,
            concrete: this.concrete,
            grading: this.grading,
            electrical: this.electrical,
            plumbing: this.plumbing,
            commercial: this.commercial,
            residential: this.residential,
            agricultural: this.agricultural
          }
          
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
