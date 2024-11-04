<script>
import Item from "./item.vue";

export default {
  data() {
    return {
      todos: [],
    };
  },
  components: {
    Item,
  },
  computed: {
    renderTodos() {
      return this.todos;
    },
  },
  methods: {
    addTodo(e) {
      if (e.target.value.trim()) {
        this.todos.unshift({
          id: Date.now(), 
          content: e.target.value,
          completed: false,
        });
        e.target.value = "";
      }
    },
    deleteTodo(id) {
      this.todos.splice(
        this.todos.findIndex((todo) => id === todo.id),
        1
      );
    },
    toggleCompletion(todo) {
      todo.completed = !todo.completed;
    },
  },
};
</script>

<template>
  <section class="containerTodo">
    <div class="containerTodoMain">
      <h2>Добавление новой незабывайКи:</h2>
      <input
        type="text"
        class="inputStyle"
        @keyup.enter="addTodo"
        autofocus="autofocus"
        title="Введите текст задачи"
        placeholder="Введите текст задачи..."
      />
    </div>
    <ul>
      <template v-if="renderTodos.length === 0">
        <h2>Забытых дел нет!</h2>
      </template>
      <template v-else>
        <Item
          v-for="todo in renderTodos"
          :todo="todo"
          :key="todo.id"
          @del="deleteTodo"
          @toggle="toggleCompletion"
        />
      </template>
    </ul>
  </section>
</template>

<style scoped>
h2 {
  text-align: left;
}

.containerTodoMain {
  border: 2px solid Gainsboro;
  width: 100%;
  margin: 2%;
  padding: 2% 5%;
  border-radius: 5px;
  box-shadow: 4px 4px 8px 0px LightSlateGray;
  background-color: Gainsboro;

  input {
    width: 100%;
    height: 25px;
  }
}

ul {
  border: 2px solid Gainsboro;
  border-radius: 5px;
  width: 50vw;
  padding: 5%;
  margin: 2%;
  box-shadow: 4px 4px 8px 0px LightSlateGray;
  background-color: Gainsboro;
  list-style-type: none;
}

ul li {
  background: rgb(169, 169, 169);
  margin-top: 2%;
}

ul li:nth-child(odd) {
  background: rgb(169, 169, 169, 0.5);
}
</style>
