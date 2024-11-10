<template>
  <section class="table-wrapper">
    <header class="table-wrapper-header">
      <h2 class="title">Countries</h2>
      <div class="pagination">
        <div class="arrow-back"></div>
        <input type="number" min="1" max="10" name="pages">
        <div class="arrow-next"></div>
      </div>
    </header>
  </section>
</template>

<script>
export default {
  name: "tableWrapper"
}
</script>

<style lang="scss" scoped>
  .table-wrapper{
    background-color: #fff;
  }
</style>