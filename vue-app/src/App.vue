<template>
  <main class="main-container">
    <section class="inner-container">
      <nav-aside/>
      <data-table/>
    </section>
  </main>
</template>

<script>


import DataTable from "@/components/dataTable";
import NavAside from "@/components/navAside";
export default {
  name: 'App',
  components: {
    NavAside,
    DataTable

  }
}
</script>

<style lang="scss">
 @use "assets/styles/index";
</style>
