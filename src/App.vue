<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-toolbar-title>Most Used Words</v-toolbar-title>
    </v-app-bar>
    <v-content>
        <TodoHome />
    </v-content>
  </v-app>
</template>

<script>
import TodoHome from './components/TodoHome.vue';
export default {
  name: 'App',

  components: {
    TodoHome
  },

  data: () => ({
    //
  }),
};
</script>
