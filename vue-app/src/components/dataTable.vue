<template>
  <table class="table-countries">
    <thead>
    <tr>
      <th>
        Common Name
      </th>
      <th>
        <img src="../assets/images/arrow_downward_alt.svg" alt="arrow down icon">
        <span>Official Name</span>
      </th>
      <th>
        <img src="../assets/images/arrow_downward_alt.svg" alt="arrow down icon">
        <span>Capital</span>
      </th>
      <th>
        <img src="../assets/images/arrow_downward_alt.svg" alt="arrow down icon">
        <span>Region</span>
      </th>
      <th>
        <img src="../assets/images/arrow_downward_alt.svg" alt="arrow down icon">
        <span>Population</span>
      </th>
      <th>
        <img src="../assets/images/arrow_downward_alt.svg" alt="arrow down icon">
        <span>Official Languages</span>
      </th>
      <th>
        <img src="../assets/images/arrow_downward_alt.svg" alt="arrow down icon">
        <span>Time Zone</span>
      </th>
      <th>
        <img src="../assets/images/arrow_downward_alt.svg" alt="arrow down icon">
      </th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="country in countriesData"
        :key="country.id"
        @click="openInGoogleMaps(country.capital)"
        tabindex="0"
        class="body-row"
    >
      <td :data-label="country.common_name">
        <div class="country-name-wrap">
          <img src="../assets/images/star.svg" alt="star icon">
          <img :src="country.flag" alt="flag icon" class="icon-flag">
          <span class="text">
            {{ country.common_name }}
          </span>
        </div>
      </td>
      <td :data-label="country.official_name">
        <span class="text">
          {{ country.official_name }}
        </span>
      </td>
      <td :data-label="country.capital">
        <span class="text">
          {{ country.capital }}
        </span>
      </td>
      <td :data-label="country.region">
        <span class="text">
          {{ country.region }}
        </span>
      </td>
      <td :data-label="country.population" class="population">
        <span class="text">
           {{ formatNumber(country.population) }}
        </span>
      </td>
      <td :data-label="country.official_language">
        <span class="text">
          {{ country.official_language }}
        </span>
      </td>
      <td :data-label="country.time_zone">
        <span class="text">
          {{ country.time_zone }}
        </span>
      </td>
    </tr>
    </tbody>
  </table>
</template>


<script>
import countries from '@/countries.json'
export default {
  name: "dataTable",
  data(){
    return {
      countriesData: countries
    }
  },
  methods: {
    openInGoogleMaps(capital){
      const url = `https://www.google.com/maps/search/?api=1&query=${encodeURIComponent(capital)}`
      window.open(url, '_blank');
    },
    formatNumber(value){
      if(value >= 1000000){
        return(value / 1000000).toFixed(1) + 'M';
      }else if(value >= 1000){
        return (value / 1000).toFixed(1) + 'K';
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@use "../assets/styles/fonts" as *;
.table-countries{
  background-color: #fff; margin: 0; padding: 0; width: 100%; table-layout: fixed;
  border: none; margin-top: 1rem;
  th, td{
    text-align: start; padding: 0.8rem;
    font-size: 1.2rem; font-family: $font-family;
  }

  th{
    line-height: 1.1; font-weight: 500; color: #9CA3AF;
    border-bottom: 1px solid #ddd;
    img{vertical-align: bottom; margin-inline-end: 0.5rem;}
  }
  .body-row{
    cursor: pointer;
    &:hover{
      background-color: #d9dadb;
    }
    &:not(:last-child){border-bottom: 1px solid #ddd;}
    td{
      font-weight: $normal;
      &:not(:first-child){
        padding-inline-start: 3rem;
      }
      .text{line-height: 1.2;}
    }
  }
  .population{
    .text{
      border: 1px solid #2E5BFF; color: #2E5BFF; padding: 0.3rem;
      width: 65px; height: 20px; display: block; text-align: center;

    }
  }
}

.icon-flag{
  width: 20px; height: 20px; border-radius: 50%;
}
.country-name-wrap{
  display: flex; gap: 8px; align-items: center;
}
@media screen and (max-width: 600px) {
  table {
    border: 0;
  }

  table caption {
    font-size: 1.3em;
  }

  table thead {
    border: none;
    clip: rect(0 0 0 0);
    height: 1px;
    margin: -1px;
    overflow: hidden;
    padding: 0;
    position: absolute;
    width: 1px;
  }

  table tr {
    border-bottom: 3px solid #ddd;
    display: block;
    margin-bottom: .625em;
  }

  table td {
    border-bottom: 1px solid #ddd;
    display: block;
    font-size: .8em;
    text-align: right;
  }

  table td::before {
    /*
    * aria-label has no advantage, it won't be read inside a table
    content: attr(aria-label);
    */
    content: attr(data-label);
    float: left;
    font-weight: bold;
    text-transform: uppercase;
  }

  table td:last-child {
    border-bottom: 0;
  }
}
</style>