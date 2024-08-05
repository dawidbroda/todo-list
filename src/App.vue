<template>
  <v-app>
    <v-container>
      <TodoList />
    </v-container>
  </v-app>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoList,
  },
};
</script>