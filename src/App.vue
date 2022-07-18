<template>
  <div>
    <h1>App根组件</h1>
    <hr />
    <todoInput @add="taskActive"></todoInput>
    <todoList :taskList="taskList"></todoList>
    <todoButton v-model:active="activeBtnIndex"></todoButton>
  </div>
</template>

<script>
import todoList from './components/to-do-list/todoList.vue'
import todoInput from './components/to-do-input/todoInput.vue'
import todoButton from './components/to-do-button/todoButton.vue'
export default {
  name: 'App',
  data() {
    return {
      list: [
        { id: 1, listName: '吃饭', state: false },
        { id: 2, listName: '睡觉', state: false },
        { id: 3, listName: '打游戏', state: false }
      ],
      //下一个任务的Id
      taskId: 4,
      // 控制按钮的状态
      activeBtnIndex: 0
    }
  },
  methods: {
    //添加任务
    taskActive(taskContent) {
      this.list.push({
        id: this.taskId,
        listName: taskContent,
        state: false
      })
      this.taskId++
    }
  },
  computed: {
    //返回筛选后的结果
    taskList() {
      switch (this.activeBtnIndex) {
        case 0:
          return this.list
        case 1:
          return this.list.filter(x => x.state)
        case 2:
          return this.list.filter(x => !x.state)
      }
    }
  },
  components: {
    todoList,
    todoInput,
    todoButton
  }
}
</script>
