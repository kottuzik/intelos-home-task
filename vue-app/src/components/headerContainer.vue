<template>
  <header class="header">
    <div class="search-wrap">
      <img src="../assets/images/search.svg" alt="search icon" class="icon-search">
      <input type="search"
             class="search"
             placeholder="Search"
             onfocus="this.placeholder=''"
             onblur="this.placeholder='Search'"
      >
    </div>
    <div class="header-menu">
      <nav class="header-menu-nav">
        <ul class="header-menu-nav-list">
          <li class="header-menu-nav-item">
            <img src="../assets/images/Dark_mode.svg" alt="dark mode icon">
          </li>
          <li class="header-menu-nav-item">
            <img src="../assets/images/Entities.svg" alt="entities icon">
          </li>
          <li class="header-menu-nav-item">
            <img src="../assets/images/notifications.svg" alt="notifications icon">
          </li>
        </ul>
      </nav>
      <div class="separator-vertical"></div>
      <button class="button-create-new">Create new</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "header-container"
}
</script>

<style lang="scss" scoped>
@use "../assets/styles/variables" as *;
  .header{
    display: flex; justify-content: space-between;
    flex-wrap: wrap; padding-top: 1.5rem;
    .search-wrap{
      display: flex; align-items: center; gap: 0.5rem; padding-inline-start: 0.5rem; border-radius: $border-radius;
      max-width: 300px; width: 100%; background-color: #D1D5DB; height: 28px;
      .icon-search{width: 20px; height: 20px;}
      &::placeholder{font-size: $font-size12;}
    }
    .search{
      border: none; width: calc(100% - 20px); height: 100%; background-color: inherit;
      &:focus{outline: none;}
    }
    &-menu{
      display: flex; gap: 1rem; margin-inline-end: 1rem; align-items: center;
    }
    .header-menu-nav-list{
      display: flex; gap: 3rem; align-items: center;
    }
    .button-create-new{
      background-color: #2C2E30; border-radius: $border-radius; color: #fff; height: 28px; min-width: 88px;
    }
    @media screen and #{$break1}{
      &-menu{margin-top: 1.5rem;}
    }
    @media screen and #{$break2open}{
      height: 63px;
    }
  }
</style>