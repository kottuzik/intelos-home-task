<template>
  <nav class="nav-aside">
    <input type="checkbox" id="openMenu" />
    <label for="openMenu" class="menu-burger" id="hamburger">
      <span></span>
      <span></span>
      <span></span>
    </label>
    <ul class="nav-list">
      <li class="nav-list-item">
        <img src="../assets/images/Overview.svg" alt="icon overview">
      </li>
      <li class="nav-list-item">
        <img src="../assets/images/Entities.svg" alt="icon entities">
      </li>
      <li class="nav-list-item">
        <img src="../assets/images/Retargeting.svg" alt="icon retargeting">
      </li>
      <li class="nav-list-item">
        <img src="../assets/images/Analysis.svg" alt="icon analysis">
      </li>
      <li class="nav-list-item">
        <img src="../assets/images/cases.svg" alt="icon cases">
      </li>
      <li class="nav-list-item">
        <img src="../assets/images/Searches.svg" alt="icon searches">
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "navAside"
}
</script>

<style lang="scss" scoped>
.nav-aside{
  position: relative; padding-top: 1rem; background-color: #fff; height: 100vh;
  .menu-burger{
    top: 1rem; inset-inline-start: 1rem;
  }
}
.nav-list{
  display: flex; flex-direction: column; gap: 2rem; align-items: center; margin-top: 3rem;
  padding-inline-end: 1rem;
}
</style>