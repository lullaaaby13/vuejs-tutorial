<template>
  <div class="container">
    <h1 class="text-center my-5">할 일 목록</h1>

    <div class="row justify-content-center">
      <div class="input-group mb-3 w-75">
        <input
          v-model="todo"
          v-on:keyup.enter="addTodo()"
          type="text"
          class="form-control todo-input"
          placeholder="오늘의 할 일은 무엇인가요?"
        >
      </div>
    </div>

    <ul class="nav nav-tabs">
      <li class="nav-item" v-for="item in ['TODO', 'PROGRESS', 'COMPLETED']">
        <a
        :class="{ 'nav-link': true, 'active': tab === item }"
        href="#"
        @click="changeTab(item)">{{ item }}</a>
      </li>
    </ul>

    <template v-if="tab === 'TODO'">
      <List
      listName="TODO"
      :list="todos"
      :startAction="changeState"
      :deleteAction="deleteTodo"
      ></List>
    </template>
    <template v-else-if="tab === 'PROGRESS'">
      <List
      listName="PROGRESS"
      :list="progresses"
      :startAction="changeState"
      :deleteAction="deleteTodo"
      ></List>
    </template>
    <template v-else-if="tab === 'COMPLETED'">
      <List
      listName="COMPLETED"
      :list="completeds"
      :startAction="changeState"
      :deleteAction="deleteTodo"
      ></List>
    </template>

  </div>
</template>

<script>
import moment from 'moment'
import List from '@/components/List.vue'

export default {
  components: {
    List,
  },
  data () {
    return  {
      todo: '',
      todoSeq: 1,
      todos: [],
      progresses: [],
      completeds: [],
      tab: 'TODO',
    }
  },
  computed: {

  },
  methods: {
    addTodo () {
      const todoName = this.todo
      const todo = {
        seq: this.todoSeq++,
        name: todoName,
        date: moment().format('YYYY-MM-DD hh:mm:ss.SSS')
      }
      this.todos.push(todo)
    },
    changeTab (tab) {
      this.tab = tab
    },
    changeState (tab, todo) {
      alert(tab)
      console.log(tab)
    },
    deleteTodo (tab, todo) {

    }
  },
}
</script>

<style>

</style>
