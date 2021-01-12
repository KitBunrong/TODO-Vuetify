<template>
  <div class="todo pa-6">
    <v-text-field
      v-model="newTaskTitle"
      class="px-2 pt-10 pb-4"
      outlined
      hide-details
      clearable
      label="Add Task"
      append-icon="mdi-plus"
      @click:append="addTask"
      @keyup.enter="addTask"
    ></v-text-field>
    <v-list flat class="pt-0">
      <div v-for="task in tasks" :key="task.id">
        <v-list-item
          @click="doneTask(task.id)"
          :class="{ 'blue lighten-5': task.done }"
        >
          <template v-slot:default>
            <v-list-item-action>
              <v-checkbox :input-value="task.done"></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{ 'text-decoration-line-through': task.done }"
              >
                {{ task.title }}
              </v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn icon @click.stop="deleteTask(task.id)">
                <v-icon color="primary">mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>
export default {
  name: "Today",
  data: () => ({
    newTaskTitle: "",
    tasks: [
      { id: 1, title: "Wake up", done: false },
      { id: 2, title: "Have Shower", done: false },
      { id: 3, title: "Go to school", done: false },
      { id: 4, title: "Back from school", done: false },
    ],
  }),
  components: {},
  methods: {
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false,
      };
      this.tasks.push(newTask);
      this.newTaskTitle = "";
    },
    doneTask(id) {
      let task = this.tasks.filter((task) => task.id === id)[0];
      task.done = !task.done;
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
  },
};
</script>

<style>
.todo {
  /* height: 140vh; */
}
</style>
