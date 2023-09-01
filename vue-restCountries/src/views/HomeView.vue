<script setup>

import { useCountriesStore } from '../stores/counter';
import { useRouter } from 'vue-router';
import { onMounted } from "vue";
import TheNavbar from '../components/TheNavbar.vue';

const router = useRouter();
const countriesStore = useCountriesStore();
//countriesStore.getCountriesData();


onMounted(() => {
  countriesStore.getCountriesData(); // Fetch countries when the component is mounted
});
</script>

<template>
  <main>
    <TheNavbar />
    <section>
      <div class="second-nav">
        <div class="input-box">
          <img src="../assets/search.svg">
          <input v-model="countriesStore.search" type="text" placeholder="Search for a country…">
        </div>
        <div class="region-box">
        <select v-model="countriesStore.selectedRegion" name="region" id="region">
          <option value="">Filter by Region</option>
          <option value="Africa">Africa</option>
          <option value="America">America</option>
          <option value="Asia">Asia</option>
          <option value="Europe">Europe</option>
          <option value="Oceania">0ceania</option>
        </select>
        </div>
        <!--<div class="region-box">
        <div class="custom-select">
          <span class="selected-option">Filter by Region</span>
          <ul class="options-list">
            <li @click="selectRegion('')">All</li>
            <li @click="selectRegion('africa')">Africa</li>
            <li @click="selectRegion('america')">America</li>
            <li @click="selectRegion('asia')">Asia</li>
            <li @click="selectRegion('europe')">Europe</li>
            <li @click="selectRegion('oceania')">Oceania</li>
          </ul>
        </div>
      </div>-->
      </div>
      
      <div v-if="countriesStore.filteredCountries.length > 0" class="card-container">
        <div @click="router.push({ name: 'detail', params: { name: country.name.common}} )" v-for="country in countriesStore.filteredCountries" :key="country.name.common" class="country-card">
          <img :src="country.flags.png" alt="flag" class="flag">
          <div class="country-info">
            <h3>{{ country.name.common }}</h3>
            <p><strong>Population:</strong> {{ country.population }}</p>
            <p><strong>Region:</strong> {{ country.region?.common }}</p>
            <p><strong>Capital:</strong> {{ country.capital?.[0] }}</p>
          </div>
          
        </div>
      </div>
      <p v-else>No results</p>
    </section>
  </main>
</template>

<style scoped>
section{
  background: #FAFAFA;
  height: 100vh;
}
.second-nav{
  display: flex;
  flex-direction: column;
  
  gap: 40px;
  padding: 24px 16px 32px 16px;
}
.input-box{
  display: flex;
  align-items: center;
  gap: 26px;
  padding: 16px 32px;
  border-radius: 5px;
  background: #FFF;
  
}
.input-box img{
  width: 15.556px;
  height: 15.556px;
}

input{
  width: 100%;
  color: #C4C4C4;
  font-family: 'Nunito Sans';
  font-size: 12px;
  font-style: normal;
  font-weight: 400;
  line-height: 20px; /* 166.667% */
  border: none;
  

}
textarea:focus, input:focus{
  outline: none;
}
/*select{
  padding: 14px 90px 14px 24px;
  border: none;
  color: #111517;
  font-family: 'Nunito Sans';
  font-size: 12px;
  font-style: normal;
  font-weight: 400;
  line-height: 20px; 
  border-radius: 5px;
  background: #FFF;
  width: 100px;
}
option{
  color: red;
  
}*/
select {
  /* Adjust the width here to reduce the width of the select dropdown */
  width: 150px;
  /* Customize the appearance of the select dropdown */
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #fff;
  color: #111517;
  font-family: 'Nunito Sans', sans-serif;
  font-size: 14px;
  font-weight: 400;
  
  background-repeat: no-repeat;
  background-position: right center;
}

/* Style the dropdown arrow */
select::-ms-expand {
  display: none;
}

/* Style option elements */
option {
  color: #111517;
  background-color: #fff;
  font-family: 'Nunito Sans', sans-serif;
  font-size: 14px;
  font-weight: 400;
}

/* Style the selected option */
select option:checked {
  background-color: #f0f0f0;
}

/* Style on focus */
select:focus {
  outline: none;
  border-color: #1e87f0;
  box-shadow: 0 0 0 2px rgba(30, 135, 240, 0.2);
}

/* Style on hover */
select:hover {
  border-color: #aaa;
}
.card-container{
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 40px;
}
.country-card{
  border: 1px solid red;
  border-radius: 5px;
  background: #FFF;
}
.country-card img{
  width: 267px;
height: 160px;
}
.country-info{
  padding: 24px 0px 48px 24px;
  display: flex;
  align-items: flex-start;
  flex-direction: column;
  gap: 8px;
  border: 1px solid red;
}
.country-info h3{
  color: #111517;
  font-family: 'Nunito Sans';
  font-size: 18px;
  font-style: normal;
  font-weight: 800;
  line-height: 26px; /* 144.444% */
}
.country-info p{
  color: #111517;
  font-family: 'Nunito Sans';
  font-size: 14px;
  font-style: normal;
  font-weight: 600;
  line-height: 16px; /* 114.286% */
}

@media (min-width: 1024px) {
.second-nav{
  flex-direction: row;
  justify-content: space-between;
  padding: 48px 80px;
}
.input-box{
  padding: 19px 200px 19px 32px;
  border: 1px solid red;
}
.input-box img{
  width: 17.5px;
  height: 17.5px;
  
}
input{
  color: #848484;
  font-size: 14px;
  width: 100%;


}

select{
  font-size: 14px;
  padding: 19px 77px 19px 24px;
  border: 1px solid red
}

}
</style>