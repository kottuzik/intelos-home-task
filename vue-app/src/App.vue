<template>
  <main class="main-container">
    <nav-aside/>
    <section class="inner-container">
      <header-container/>
      <table-wrapper/>
    </section>
  </main>
</template>

<script>


import NavAside from "@/components/navAside";
import TableWrapper from "@/components/tableWrapper";
import HeaderContainer from "@/components/headerContainer";
export default {
  name: 'App',
  components: {
    HeaderContainer,
    TableWrapper,
    NavAside,
  }
}
</script>

<style lang="scss">
 @use "assets/styles/index";
</style>
<style lang="scss" scoped>
  .main-container{
    display: flex; gap: 1rem;
  }
  .inner-container{
    display: flex; flex-direction: column; gap: 1rem;
  }
</style>
