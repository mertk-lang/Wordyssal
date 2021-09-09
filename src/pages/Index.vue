<template>
  <div class="">
    <q-page class="justify-center flex">
      <Search></Search>
    </q-page>
  </div>
</template>

<script>
import Search from '../components/Search.vue'

export default {
  components: {
    Search
  }
}

</script>

<style lang="sass">
   .q-header
     background: linear-gradient(to right, #000000, #434343)
</style>
