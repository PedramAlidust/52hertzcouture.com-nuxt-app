<template>
    <!-- navigation section -->
    <nav class="navbar navbar-expand-lg bg-white py-3">
      <div class="container pe-5 pe-lg-0">
        <button
          class="nav-border p-0"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navmenu"
        >
          <i class="bi-2x bi-list display-6"></i>
        </button>
        <div class="collapse navbar-collapse" id="navmenu">
          <ul class="navbar-nav pe-lg-4 pe-md-4">
            <li v-for="menu_item in menu_data.slice().reverse()" :key="menu_item.id" class="nav-item pe-lg-2 pe-md-2">
              <a :href="menu_item.acf.menu_link" class="nav-link active-item text-dark">{{menu_item.acf.menu_text}}</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
</template>

<script>

export default {
  name: "TheHeader",
  props: ['menu_data']
};
</script>


<style scoped>

</style>
