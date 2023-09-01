<script setup>
import TheNavbar from '../components/TheNavbar.vue';
import { useRoute } from 'vue-router';
import { useCountriesStore } from '../stores/counter';
import { onMounted } from 'vue';
const route = useRoute();

const countryStore = useCountriesStore();
countryStore.updateCountry(route.params.name);

//countryStore.getCountryData()


onMounted(() => {
    countryStore.getCountryData();
})


</script>

<template>
  <main>
    <TheNavbar />
    <!--<div>
        <p>{{ countryStore.countryData[0]?.name.common }}</p>
    </div>-->
    <div class="country-details">
      <img :src="countryStore.countryData[0]?.flags.png" :alt="countryStore.countryData[0]?.name.common" class="flag">
      <div class="details">
        <h2>{{ countryStore.countryData[0]?.name.common }}</h2>
        <p><strong>Native Name:</strong> {{ countryStore.countryData[0]?.name.nativeName }}</p>
        <p><strong>Population:</strong> {{ countryStore.countryData[0]?.population }}</p>
        <p><strong>Region:</strong> {{ countryStore.countryData[0]?.region }}</p>
        <p><strong>Subregion:</strong> {{ countryStore.countryData[0]?.subregion }}</p>
        <p><strong>Capital:</strong> {{ countryStore.countryData[0]?.capital[0] }}</p>
        <p><strong>Top Level Domain:</strong> {{ countryStore.countryData[0]?.tld[0] }}</p>
        <p><strong>Languages:</strong></p>
        <ul>
          <li v-for="language in countryStore.countryData[0]?.languages" :key="language">
            {{ language }}
          </li>
        </ul>
        <p><strong>Border Countries:</strong></p>
        <ul>
          <li v-for="borderCountry in countryStore.countryData[0]?.borders" :key="borderCountry">
            {{ borderCountry }}
          </li>
        </ul>
      </div>
      </div>
  </main>
</template>

<style>
@media (min-width: 1024px) {

}
</style>
