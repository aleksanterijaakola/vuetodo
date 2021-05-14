<template>
  <div
    class="w-24 md:w-auto h-100 w-full min-h-screen flex items-center justify-center bg-teal-lightest font-sans"
  >
    <div class="container bg-white rounded shadow p-6 m-4 w-full lg:w-3/4 lg:max-w-lg">
      <div class="mb-4">
        <h1 class="text-grey-darkest">Kauppalista</h1>
        <div class="flex mt-4">
          <input
            class="shadow appearance-none border rounded w-full py-2 px-3 mr-4 text-grey-darker"
            placeholder="Add Todo"
            v-model="newToDo"
          />
          <button
            class="flex-no-shrink p-2 border-2 rounded text-teal border-teal"
            v-on:click="addToDo()"
          >
            Add
          </button>
        </div>
      </div>
      <div>
        <li
          class="flex mb-4 items-center"
          v-for="(todo, i) in existingToDo"
          :key="i"
        >
          <span class="w-full text-grey-darkest">{{ todo.text }}</span>
          <button
            class="flex-no-shrink border-red-500 p-2 ml-2 border-2 rounded text-red hover:text-white hover:bg-red"
            @click="deleteToDo()"
          >
            Remove
          </button>
        </li>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  data() {
    return {
      newToDo: "",
      existingToDo: [],
    };
  },
  methods: {
    addToDo() {
      this.existingToDo.push({
        text: this.newToDo,
      }),
        (this.newToDo = "");
    },
    deleteToDo(i) {
      this.existingToDo.splice(i, 1);
    },
  },
};
</script>
