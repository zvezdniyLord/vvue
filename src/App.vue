<script>
import HelloWorld from "./components/HelloWorld.vue";
import Todo from "./components/Todo.vue";

export default {
  data() {
    return {
      currentTemplate: 1,
    };
  },
  components: {
    HelloWorld,
    Todo,
  },
  methods: {
    showTemplate1() {
      this.currentTemplate = 1;
    },
    showTemplate2() {
      this.currentTemplate = 2;
    },
  },
};
</script>

<template>
  <div class="container">
    <button @click="showTemplate1">Страница приветствия</button>
    <button @click="showTemplate2">Список задач</button>

    <HelloWorld msg="Это текст из Aрр" v-if="currentTemplate === 1" />
    <Todo v-else-if="currentTemplate === 2" />
  </div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
