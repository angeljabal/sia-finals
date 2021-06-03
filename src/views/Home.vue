<template>
  <main v-if="!loading" class="container p-2">
    <DataTitle :text="title" :dataDate="dataDate"/>
    <DataBoxes :stats="stats"/>

    <CountrySelect @get-country="getCountryData" :countries="countries"/>
    <div class="col-md-6 offset-md-3">
    <button @click="clearCountryData" v-if="stats.Country" class="btn btn-success" style="margin-left: 25px">
      Clear Country
    </button>
    </div>
    
  </main>
  <main class="flex flex-sm-col align-center justify-center text-center" v-else>
    <div class="mt-10 mb-6">
      Fetching Data
    </div>
    <img :src="loadingImage" class="w-24 m-auto" alt="">
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
import CountrySelect from '@/components/CountrySelect'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect
  },
  data() {
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif')
    }
  },
  methods: {
    async fetchCovidData(){
      const response = await fetch('https://api.covid19api.com/summary')
      const data = await response.json()
      return data 
    },

    getCountryData(country){
      this.stats = country
      this.title = country.Country
    },

    async clearCountryData(){
      this.loading = true
      const data = await this.fetchCovidData()
      this.title = "Global"
      this.stats = data.Global
      this.loading = false
    }
  },
  async created(){
    const data = await this.fetchCovidData()

    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}

</script>
