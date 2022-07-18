  <template>
    <div>
      <ul class="list-group">
        <li class="list-group-item d-flex justify-content-between align-items-center" v-for="item in taskList" :key="item.id">
          <input type="checkbox" :id="item.id" v-model="item.state" />
          <label :for="item.id" :class="item.state ? 'del' : ''">{{ item.listName }}</label>
          <span class="badge badge-success badge-pill" v-if="item.state">已完成</span>
          <span class="badge badge-warning badge-pill" v-else>未完成</span>
        </li>
      </ul>
    </div>
  </template>

  <script>
  export default {
    props: ['taskList'],
    name: 'todoList'
  }
  </script>

  <style lang="less" scoped>
  li {
    width: 400px;
  }
  .del {
    text-decoration: line-through;
    font-style: italic;
    color: gray;
  }
  </style>
