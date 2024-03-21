<template>
  <div>
    <h1>Список задач</h1>
    <div class="add__todo">
      <input type="text" v-model="newTodo" placeholder="Добавь задачу" />
      <button @click="addTodo">Добавить задачку</button>
    </div>
    <ul>
    <h2 class="todoh2">Задачи</h2>
      <li class="td" v-for="(todo, index) in todos" :key="index">
        <div class="tdd">
          <span class="todo__data"> {{ todo }}</span>
          <button @click="editTodo(index)">Редактировать</button>
          <button @click="deleteTodo(index)">Удалить</button>
        </div>
      </li>
    </ul>
    <h4 v-if="todos.length === 0">Пусто</h4>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  mounted() {
    this.todos = JSON.parse(localStorage.getItem("todos")) || [];
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.push(this.newTodo.trim());
        this.saveTodos();
        this.newTodo = "";
      }
    },
    editTodo(index) {
      const updatedTodo = prompt("Edit todo", this.todos[index]);
      if (updatedTodo !== null) {
        this.todos[index] = updatedTodo;
        this.saveTodos();
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
      this.saveTodos();
    },
    saveTodos() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
  },
};
</script>
