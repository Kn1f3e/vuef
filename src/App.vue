<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title>Книжный магазин</v-toolbar-title>
    </v-toolbar>
    <Bookstore />
  </v-app>
</template>

<script>
import Bookstore from './components/Bookstore.vue';

export default {
  components: {
    Bookstore
  }
};
</script>
