<template>
  <div class="button-container mt-3">
    <div class="btn-group">
      <button type="button" class="btn" :class="active === 0 ? 'btn-primary' : 'btn-secondary'" @click="onBtnClick(0)">全部</button>
      <button type="button" class="btn" :class="active === 1 ? 'btn-primary' : 'btn-secondary'" @click="onBtnClick(1)">已完成</button>
      <button type="button" class="btn" :class="active === 2 ? 'btn-primary' : 'btn-secondary'" @click="onBtnClick(2)">未完成</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'todoButton',
  props: {
    active: {
      type: Number,
      required: true,
      // 默认激活索引值为 0 的按钮（全部：0，已完成：1，未完成：2）
      defalut: 0
    }
  },
  emits: ['update:active'],
  methods: {
    //传输按钮的index值给App组件
    onBtnClick(index) {
      if (index === this.active) return
      this.$emit('update:active', index)
    }
  }
}
</script>

<style lang="less" scoped>
.button-container {
  width: 400px;
  text-align: center;
}
</style>
