<template>
  <table class="table-countries">
    <thead>
    <tr>
      <th>
        Common Name
      </th>
      <th>
        Official Name
      </th>
      <th>
        Capital
      </th>
      <th>
        Region
      </th>
      <th>
        Population
      </th>
      <th>
        Official Languages
      </th>
      <th>
        Time Zone
      </th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="country in countriesData"
        :key="country.id"
        @click="openInGoogleMaps(country.capital)"
        style="cursor: pointer;"
        tabindex="0"
    >
      <td :data-label="country.common_name">
        <div class="country-name-wrap">
          <img :src="country.flag" alt="flag icon" class="icon-flag">
          {{ country.common_name }}
        </div>
      </td>
      <td :data-label="country.official_name">{{ country.official_name }}</td>
      <td :data-label="country.capital">{{ country.capital }}</td>
      <td :data-label="country.region">{{ country.region }}</td>
      <td :data-label="country.population">{{ country.population }}</td>
      <td :data-label="country.official_language">{{ country.official_language }}</td>
      <td :data-label="country.time_zone">{{ country.time_zone }}</td>
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
    }
  }
}
</script>

<style lang="scss" scoped>
table {
  border: 1px solid #ccc;
  border-collapse: collapse;
  margin: 0;
  padding: 0;
  width: 100%;
  table-layout: fixed;
}

table caption {
  font-size: 1.5em;
  margin: .5em 0 .75em;
}

table tr {
  background-color: #f8f8f8;
  border: 1px solid #ddd;
  padding: .35em;
}

table th,
table td {
  padding: .625em;
  text-align: start;
}

table th {
  font-size: .85em;
  letter-spacing: .1em;
  text-transform: uppercase;
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