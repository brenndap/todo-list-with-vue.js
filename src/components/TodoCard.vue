<template>
  <div class="card">
    <header class="card-header">
      <p class="card-header-title has-text-left">{{today}}</p>
      <div class="has-text-right">
        <p
          class="card-header-title"
        >{{`${ todos.length } ${todos.length > 1 ? "tarefas" : "tarefa"}`}}</p>
      </div>
    </header>
    <div class="card-content">
      <div class="content">
        <new-todo @addTodo="addTodo"></new-todo>
      </div>
      <div class="content">
          <todo-list :todos="todos" @check="checkTodo" @remove="removeTodo"></todo-list>
      </div>
    </div>
  </div>
</template>

<script>    
import NewTodo from "./NewTodo";
import TodoList from './TodoList'

export default {
  name: "todo-card",
  components: {
    NewTodo,
    TodoList
  },
  data() {
    return {
      dias: [
        "Domingo",
        "Segunda",
        "Terça",
        "Quarta",
        "Quinta",
        "Sexta",
        "Sábado"
      ],
      meses: [
        "Janeiro",
        "Fevereiro",
        "Março",
        "Abril",
        "Maio",
        "Junho",
        "Julho",
        "Agosto",
        "Setembro",
        "Outubro",
        "Novembro",
        "Dezembro"
      ],
      todos: []
    };
  },
  computed: {
    today: function() {
      let newDate = new Date();
      return `${this.dias[newDate.getDay()]}, ${newDate.getDate()} de ${
        this.meses[newDate.getMonth()]
      }`;
    }
  },
  methods: {
    addTodo(todo) {
      let newTodo = { description: todo, checked: false };
      this.todos.push(newTodo)
    },
    checkTodo(idx){
        this.todos[idx]['checked'] = !this.todos[idx]['checked']
    },
    removeTodo(idx){
        this.todos.splice(idx, 1)
    }
  }
};
</script>

<style>
.card {
  border-radius: 10px;
}
.card-header-title {
  color: #636368;
}
</style>