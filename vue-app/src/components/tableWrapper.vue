<template>
  <section class="table-wrapper">
    <header class="table-wrapper-header">
      <h2 class="title">Countries</h2>
      <div class="pagination">
        <div class="light-border arrow arrow-back">
          <img src="../assets/images/chevron_left.svg" alt="arrow back icon">
        </div>
        <input type="number" min="1" max="10" name="pages" class="light-border page-num">
        <div class="light-border arrow arrow-next">
          <img src="../assets/images/chevron_right.svg" alt="arrow next icon">
        </div>
      </div>
    </header>
    <data-table/>
  </section>
</template>

<script>
import DataTable from "@/components/dataTable";
export default {
  name: "tableWrapper",
  components: {DataTable}
}
</script>

<style lang="scss" scoped>
  .table-wrapper{
    background-color: #fff; padding: 1rem;
    &-header{
      display: flex; justify-content: space-between; flex-wrap: wrap;
      .pagination{
        display: flex; gap: 5px; height: 28px;
        *{
          display: flex; align-items: center; height: 100%;
          border-radius: 3px;
        }
      }
      .page-num{
        width: 60px;
      }
      .arrow{width: 28px; height: 28px; justify-content: center;}
    }
  }
</style>