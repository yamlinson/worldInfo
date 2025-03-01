<script setup lang="ts">
  import WorldMap from '../components/WorldMap.vue';
  import axios from 'axios';
  import { ref } from 'vue';
  import { Country } from '../Country';

  const country = ref<Country>({
    id: '',
    name: '',
    capital: '',
    region: '',
    income: '',
    population: '',
    gdp: ''
  });

  const fetchData = async (url: string) => {
    try {
      const response = await axios.get(url);
      return response.data;
    } catch (error) {
      console.error('Error fetching data:', error);
    }
  };

  const getCountry = async (id: string) => {
    const apiRoot = 'https://api.worldbank.org/v2/country/';
    const apiUrlMain = `${apiRoot}${id}?format=json`;
    const apiUrlPop = `${apiRoot}${id}/indicator/SP.POP.TOTL?date=2022&format=json`
    const apiUrlGdp = `${apiRoot}${id}/indicator/NY.GDP.MKTP.CD?date=2022&format=json`

    var countryData;
    var countryPop;
    var countryGdp;

    var data = await fetchData(apiUrlMain);
    if (data && data[1] && data[1][0]) {
      countryData = data[1][0];
    }

    data = await fetchData(apiUrlPop);
    if (data && data[1] && data[1][0]) {
      countryPop = data[1][0];
    }

    data = await fetchData(apiUrlGdp);
    if (data && data[1] && data[1][0]) {
      countryGdp = data[1][0];
    }

    country.value = {
      id: id,
      name: countryData.name,
      capital: countryData.capitalCity,
      region: countryData.region.value,
      income: countryData.incomeLevel.value,
      population: insertCommas(countryPop.value),
      gdp: insertCommas(countryGdp.value)
    };

  };

  function insertCommas(num: number) {
    var parts = num.toString().split(".");
    parts[0] = parts[0].replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    return parts.join(".");
  }
</script>

<template>
  <main>
    <div id="info" class="card">
      <div v-if="!country.id">
        <p class="info">Please select a country</p>
      </div>
      <div v-else>
        <h2>{{ country.name }}</h2>
        <br>
        <h3>Capital:</h3>
        <p>{{ country.capital }}</p>
        <h3>Region:</h3>
        <p>{{ country.region }}</p>
        <h3>Income:</h3>
        <p>{{ country.income }}</p>
        <h3>Population:</h3>
        <p>{{ country.population }}</p>
        <h3>GDP:</h3>
        <p>{{ country.gdp }}</p>
      </div>
    </div>
    <div class="map">
      <WorldMap @locationChanged="getCountry"/>
    </div>
  </main>
</template>

<style>
  .card {
    background-color: #eeedf9;
    margin: 40px;
    padding: 20px;
    border: 1px solid #2d2a32;
    border-radius: 10px;
  }

  .card h2 {
    text-align: center;
  }

  p.info {
    text-align: center;
    font-weight: bold;
  }

  .map {
    margin: 40px;
  }
</style>
