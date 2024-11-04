<script>
export default {
  methods: {
    deleteTodo() {
      this.$emit("del", this.todo.id);
    },
    toggle() {
      this.$emit("toggle", this.todo);
    },
  },
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
};
</script>

<template>
  <li :class="{ completed: todo.completed }">
    <div class="todoList">
      <span>{{ todo.content }}</span>
      <label class="custom-checkbox" title="Отметить задачу выполненой">
        <input type="checkbox" :checked="todo.completed" @change="toggle" />
        <span class="checkmark"></span>
      </label>
      <button @click="deleteTodo" class="delete-button" title="Удалить задачу">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="20"
          height="20"
          fill="currentColor"
          class="bi bi-x-lg"
          viewBox="0 0 16 16"
        >
          <path
            d="M2.146 2.854a.5.5 0 1 1 .708-.708L8 7.293l5.146-5.147a.5.5 0 0 1 .708.708L8.707 8l5.147 5.146a.5.5 0 0 1-.708.708L8 8.707l-5.146 5.147a.5.5 0 0 1-.708-.708L7.293 8z"
          />
        </svg>
      </button>
    </div>
  </li>
</template>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Playwrite+GB+S:ital,wght@0,100..400;1,100..400&display=swap");

.todoList {
  display: grid;
  grid-template-columns: 5fr 0.5fr 0.5fr;
  font-family: "Playwrite GB S", cursive;
  border: none;
  padding: 5px;
}

.custom-checkbox {
  position: relative;
  display: inline-block;
}

.custom-checkbox input {
  opacity: 0;
  width: 0;
  height: 0;
}

.checkmark {
  display: inline-block;
  transition: background-color 0.3s, border-color 0.3s; /* Плавный переход */
  content: "";
  position: absolute;
  left: 6px; 
  top: -1px; 
  width: 13px; 
  height: 20px; 
  border: solid black; 
  border-width: 0 2px 2px 0; 
  transform: rotate(45deg);
}

.checkmark:hover {
  border-color: DarkGreen;
}

.custom-checkbox input:checked:hover + .checkmark {
  border-color: DarkGreen; 
}

.delete-button {
  border: none;
  background: inherit;
}

.delete-button:hover {
  color: red;
  transition: color 0.3s;
}

.completed {
  text-decoration: line-through;
  background-color: rgb(144, 238, 144, 0.5) !important;
  opacity: 0.6;
}
</style>
