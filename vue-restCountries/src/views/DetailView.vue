<script setup>
import TheNavbar from '../components/TheNavbar.vue';
import { useRoute } from 'vue-router';
import { useCountriesStore } from '../stores/counter';
import { onMounted } from 'vue';
import { RouterLink, RouterView } from 'vue-router'
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
    <section>
    <div class="box">
      <div class="btn">
        <RouterLink to="/"><button><img src="../assets/call-made.svg">Back</button></RouterLink>
      </div>
    
    <div class="country-details">
      <img :src="countryStore.countryData[0]?.flags.png" :alt="countryStore.countryData[0]?.name.common" class="flag">
      <div class="details">
        <h2>{{ countryStore.countryData[0]?.name.common }}</h2>
        <div class="big-text">
        <div class="text-1">
        <p><strong>Native Name:</strong> <span v-for="nativeName in countryStore.countryData[0]?.name.nativeName" :key="nativeName">{{ nativeName.official }}</span></p>
        <p><strong>Population:</strong> {{ countryStore.countryData[0]?.population }}</p>
        <p><strong>Region:</strong> {{ countryStore.countryData[0]?.region }}</p>
        <p><strong>Subregion:</strong> {{ countryStore.countryData[0]?.subregion }}</p>
        <p><strong>Capital:</strong> {{ countryStore.countryData[0]?.capital[0] }}</p>
        </div>
        <div class="text-2">
        <p><strong>Top Level Domain:</strong> {{ countryStore.countryData[0]?.tld[0] }}</p>
        <div class="lang">
        <p><strong>Languages:</strong></p>
        <ul>
          <li v-for="language in countryStore.countryData[0]?.languages" :key="language">
            {{ language }}
          </li>
        </ul>
        </div>
        </div>
        </div>
        <div class="b-countries">
          <p><strong>Border Countries:</strong></p>
          <ul>
            <li v-for="borderCountry in countryStore.countryData[0]?.borders" :key="borderCountry">
              {{ borderCountry }}
            </li>
          </ul>
        </div>
        
      </div>
      </div>
      </div>
      </section>
  </main>
</template>

<style scope>
section{
  background: #FAFAFA;
  height: 150vh;
}

.country-details{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  /*border: 1px solid red;*/
  gap: 20px;
  padding: 0px 20px;
  
}
.country-details img{
  width: 319.837px;
  height: 275.924px;
  /*border: 1px solid red;*/
}
.details{
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  /*border: 1px solid red;*/
  gap: 16px;
}
.details h2{
  color: #111517;
  font-family: 'Nunito Sans';
  font-size: 22px;
  font-style: normal;
  font-weight: 800;
  line-height: normal;

}
.text-1{
  display: flex;
  flex-direction: column;

}

.text-1 p{
  
font-family: 'Nunito Sans';
font-size: 14px;
font-style: normal;
font-weight: 600;
line-height: 32px; /* 228.571% */
}
.text-2 {
  display: flex;
  flex-direction: column;
  gap: 5px;
}
.text-2 p{
  
font-family: 'Nunito Sans';
font-size: 14px;
font-style: normal;
font-weight: 600;
line-height: 32px; /* 228.571% */
}
.lang{
  display: flex;
  gap: 5px;
}
.lang ul{
  display: flex;
  gap: 5px;
}
.lang ul li{
  list-style: none;
  font-family: 'Nunito Sans';
font-size: 14px;
font-style: normal;
font-weight: 600;
line-height: 32px; 
}
.b-countries{
  display: flex;
  flex-direction: column;
  gap: 10px;
}
.b-countries ul{
  display: flex;
  list-style: none;
  gap: 10px;
  flex-wrap: wrap;
}
.b-countries ul li{
  border-radius: 2px;
background: #FFF;
padding: 6px 30px;
box-shadow: 0px 0px 4px 1px rgba(0, 0, 0, 0.10);
}
button{
  display: flex;
  gap: 9px;
  padding: 8px 24px;
  border-radius: 2px;
background: #FFF;
box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.29);
border: none;
}
.btn{
  padding: 40px 0px 64px 24px;
}
.btn a{
  text-decoration: none;
}
@media (min-width: 1024px) {
.country-details{
  flex-direction: row;
  justify-content: center;
  gap: 100px;
}

.text-1{
  flex-direction: column;
  padding: 0px;
}
.text-2{
  display: flex;
  flex-direction: column;
  /*border: 1px solid red;*/
}
.country-details img{
  width: 559.715px;
height: 483.169px;
}
.big-text{
  display: flex;
  justify-content: space-between;
  gap: 40px;
  
}

}
</style>
