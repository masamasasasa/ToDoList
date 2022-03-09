<template>
  <!-- 查看任务选项 -->
  <div class="mt-3 btn-container button-style">
    <div class="button-group" role="group" aria-label="Basic example">
      <button type="button" :class="active === 0 ? 'btn btn-primary' : 'btn btn-default'" @click="onBtnClick(0)">全部</button>
      <button type="button" :class="active === 1 ? 'btn btn-primary' : 'btn btn-default'" @click="onBtnClick(1)">已完成</button>
      <button type="button" :class="active === 2 ? 'btn btn-primary' : 'btn btn-default'" @click="onBtnClick(2)">未完成</button>
    </div>
  </div>

</template>

<script>
export default {
  name: 'todoButton',
  emit: ['update:active'],
  props: {
    active: {
      type: Number,
      required: true,
      //激活项的索引值：全部：0 已完成：1  未完成： 2（默认为0）
      default: 0
    }
  },
  methods: {
    onBtnClick(index) {
      if (index === this.active) return
      this.$emit('update:active', index)
    }
  }
}
</script>

<style lang='less' scoped>
.button-style {
  padding-top: 30px;
}

.btn:focus {
  outline: none;
  border-color: rgb(0, 123, 255);
  box-shadow: 0 0;
}
</style>