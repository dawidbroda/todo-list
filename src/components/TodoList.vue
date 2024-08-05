<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="8" offset-md="2">
        <v-card>
          <v-card-title>
            <v-text-field
              v-model="newTask"
              label="New Task"
              @keyup.enter="addTask"
              clearable
            ></v-text-field>
          </v-card-title>
          <v-card-text>
            <v-list>
              <v-list-item
                v-for="(task, index) in tasks"
                :key="index"
                @click="toggleTaskCompletion(index)"
              >
                <v-list-item-content>
                  <v-list-item-title :class="{ 'completed-task': task.completed }">
                    {{ task.text }}
                  </v-list-item-title>
                </v-list-item-content>
                <v-list-item-action>
                  <v-btn icon @click.stop="removeTask(index)">
                    <v-icon>mdi-delete</v-icon>
                  </v-btn>
                </v-list-item-action>
              </v-list-item>
            </v-list>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      newTask: '',
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask.trim(), completed: false });
        this.newTask = '';
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
    toggleTaskCompletion(index) {
      this.tasks[index].completed = !this.tasks[index].completed;
    },
  },
};
</script>

<style scoped>
  .completed-task {
    text-decoration: line-through;
    color: grey;
  }
</style>
