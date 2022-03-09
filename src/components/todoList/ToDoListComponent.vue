<template>
  <!-- todolist组件 -->
  <div>
    <div :class="style=='☀' ? 'todolist' : 'todolist-night'">
      <span class="changeStyle" @click="changeStyle">{{style}}</span>
      <h1>ToDoList</h1>
      <todoinput @add="onAddNewData"></todoinput>
      <todolist :listdata="tasklist" @remove="deleteData"></todolist>
      <todobutton v-model:active="activeIndex"></todobutton>
    </div>
  </div>
</template>

<script>
import todolist from './todo-list.vue'
import todoinput from './todo-input.vue'
import todobutton from './todo-button.vue'

export default {
  components: {
    todolist,
    todoinput,
    todobutton
  },
  data() {
    return {
      todolist: [
        { id: 1, task: '周一早晨9点开会', done: false },
        { id: 2, task: '周一晚上8点聚餐', done: false },
        { id: 3, task: '准备周三上午的演讲稿', done: true }
      ],
      nextId: 4,
      activeIndex: 0,
      //true 为日间模式  false 为夜间模式
      style: '☀'
    }
  },
  methods: {
    onAddNewData(taskname) {
      this.todolist.push({ id: this.nextId, task: taskname, done: false })
      this.nextId++
    },
    deleteData(id) {
      this.todolist = this.todolist.filter(item => item.id !== id)
    },
    changeStyle() {
      if (this.style == '☀') {
        this.style = '🌙'
      } else {
        this.style = '☀'
      }
    }
  },
  computed: {
    tasklist() {
      switch (this.activeIndex) {
        case 0:
          return this.todolist
        case 1:
          return this.todolist.filter(x => x.done)
        case 2:
          return this.todolist.filter(x => !x.done)
      }
    }
  }
}
</script>

<style lang='less' scoped>
</style>