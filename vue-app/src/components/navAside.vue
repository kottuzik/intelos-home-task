<template>
  <nav class="nav-aside">
    <div class="menu-burger" id="hamburger">
      <span></span>
      <span></span>
      <span></span>
    </div>
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
    top: 1rem; inset-inline-start: 1.5rem;
  }
}
.nav-list{
  display: flex; flex-direction: column; gap: 2rem; align-items: center; margin-top: 5rem;
  padding-inline-end: 1rem; width: 63px;
  &-item{
    &:not(:last-child){
      width: 24px; height: 24px;
    }
    &:last-child{
      width: 48px; height: 42px; padding-inline-start: 0.4rem;
    }
  }
}
</style>