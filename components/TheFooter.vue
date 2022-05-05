<template>
 <!-- Copyright Footer -->
    <div class="container-full bg-light mt-5">
      <div class="container text-center">
        <div class="row align-items-center">
          <div class="col-12 mt-3">
            <p>{{ footer_data[0].acf.copyright }}</p>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
    props: ['footer_data']
}
</script>

<style scoped>

</style>