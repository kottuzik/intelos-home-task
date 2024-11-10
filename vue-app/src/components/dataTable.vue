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
      <td data-label="Common Name">
        <div class="country-name-wrap">
          <img src="../assets/images/star.svg" alt="star icon">
          <img :src="country.flag" alt="flag icon" class="icon-flag">
          <span class="text">
            {{ country.common_name }}
          </span>
        </div>
      </td>
      <td data-label="Official Name">
        <span class="text">
          {{ country.official_name }}
        </span>
      </td>
      <td data-label="Capital">
        <span class="text">
          {{ country.capital }}
        </span>
      </td>
      <td data-label="Region">
        <span class="text">
          {{ country.region }}
        </span>
      </td>
      <td data-label="Population" class="population">
        <span class="text">
           {{ formatNumber(country.population) }}
        </span>
      </td>
      <td data-label="Official Languages">
        <span class="text">
          {{ country.official_language }}
        </span>
      </td>
      <td data-label="Time Zone">
        <span class="text">
          {{ country.time_zone }}
        </span>
      </td>
      <td class="view-on-map">
        <p class="t-text desktop-hide">View on map</p>
        <n-tooltip trigger="hover" :show-arrow="false">
          <template #trigger>
            <span class="text">...</span>
          </template>
          View on map
        </n-tooltip>
      </td>
    </tr>
    </tbody>
  </table>
</template>


<script>
import countries from '@/countries.json'
export default {
  name: "dataTable",
  components: {

  },
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
@use "../assets/styles/variables" as *;
.table-countries{
   margin: 0; padding: 0; width: 100%; table-layout: fixed;
  border: none; margin-top: 1rem;
  th, td{
    text-align: start; padding: 0.8rem;
    font-size: 1.2rem; font-family: $font-family;
  }

  th{
    line-height: 1.1; font-weight: 500; color: #9CA3AF;
    border-bottom: 1px solid #D1D5DB;
    img{vertical-align: bottom; margin-inline-end: 0.5rem;}
  }
  .body-row{
    cursor: pointer;
    &:hover{
      background-color: #d9dadb;
    }
    td{
      font-weight: $normal;
      &:not(:first-child){
        padding-inline-start: 3rem;
      }
      .text{line-height: 1.2;}
      &.view-on-map{
        padding-inline-start: 1.5rem; position: relative;
        &:before{
          content: '';
          background-image: url("../assets/images/visibility.svg"); background-size: contain;
          width: 20px; height: 20px; position: absolute; background-repeat: no-repeat;
        }
        &:hover{
          .text{opacity: 0;}
          &:before{display: block;}
        }
      }
    }

  }
  .population{
    .text{
      border: 1px solid #2E5BFF; color: #2E5BFF; padding: 0.3rem; border-radius: $border-radius;
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
@media screen and #{$break1} {
  .table-countries {
    thead {
      clip: rect(0 0 0 0); height: 1px; width: 1px;
      margin: -1px; overflow: hidden;
      padding: 0; position: absolute;
    }
    tr{
      display: block;
      margin-bottom: 3rem; border: 1px solid #D1D5DB; border-bottom: 3px solid #ddd;
      border-radius: $border-radius;
    }
    td{
      border-bottom: 1px solid #D1D5DB; display: block;
      &:before{
        /* * aria-label has no advantage, it won't be read inside a table
        content: attr(aria-label); */
        content: attr(data-label); font-weight: $bold; text-transform: uppercase;
        padding-bottom: 1rem;
      }
      .text{display: block; margin-top: 0.5rem;}
      &:last-child {border-bottom: 0;}
      .country-name-wrap{
        margin-top: 0.7rem;
      }
    }
    td.view-on-map{
      display: flex; justify-content: space-between;
      .t-text{font-weight: $bold; font-size: 1.4rem; margin-inline-start: 1.5rem;}
      .text{display: none;}
      &:before{inset-inline-end: 1rem;}
    }
  }
}
@media screen and #{$break2open}{
  .table-countries{
    background-color: #fff;
    .body-row{
      &:not(:last-child){border-bottom: 1px solid #D1D5DB;}
      td.view-on-map{
        &:before{
          display: none; inset-inline-start: 1rem;
        }
      }
    }
  }
}
</style>