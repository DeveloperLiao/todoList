<template>
  <div>
    <form @submit.prevent="addTask">
      <div class="form-row align-items-center">
        <div class="col-auto">
          <div class="input-group mb-2">
            <div class="input-group-prepend">
              <div class="input-group-text">任务</div>
            </div>
            <input type="text" class="form-control" id="inlineFormInputGroup" placeholder="输入你将要完成的任务" v-model.trim="taskContent" />
          </div>
        </div>
        <div class="col-auto">
          <button type="submit" class="btn btn-primary mb-2">提交</button>
        </div>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'todoInput',
  data() {
    return { taskContent: '' }
  },
  emits: ['add'],
  methods: {
    //传输需要添加的任务给App组件
    addTask() {
      if (!this.taskContent) return alert('输入的内容不能为空！')
      this.$emit('add', this.taskContent)
      this.taskContent = ''
    }
  }
}
</script>

<style lang="less" scoped></style>
