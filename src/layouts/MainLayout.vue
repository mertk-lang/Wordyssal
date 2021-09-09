<template>
   <div class=".page">
     <q-layout view="lHh lpr lFf"  style="" class="">
      <q-header class="text-grey-1" bordered>
        <q-toolbar class="container">
          <q-toolbar-title class="text-permanent text-bold text-center">
            Wordyssal
          </q-toolbar-title>
        </q-toolbar>
      </q-header>


      <q-page-container class="bg-dark">
         <router-view />
      </q-page-container>
    </q-layout>
  </div>
</template>

<script>

export default {
  name: 'MainLayout',

  components: {

  },

}
</script>

<style lang="sass">
 .q-header
   background: linear-gradient(to right, #000000, #434343)

</style>
