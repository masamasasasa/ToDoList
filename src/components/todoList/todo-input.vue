<template>
  <!-- 添加新任务 -->
  <div>
    <form class="form-inline form-style" @submit.prevent="onFormSubmit">
      <div class="input-group mb-2 mr-sm-2">
        <div class="input-group-prepend">
          <div class="input-group-text">任务</div>
        </div>
        <input type="text" class="form-control input-style" placeholder="请填写任务信息" v-model.trim="taskname">
      </div>
      <button type="submit" class="btn mb-2">添加新任务</button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'todoInput',
  emits: ['add'],
  data() {
    return {
      taskname: ''
    }
  },
  methods: {
    onFormSubmit() {
      if (!this.taskname) return alert('任务名称不能为空')
      this.$emit('add', this.taskname)
      this.taskname = ''
    }
  }
}
</script>

<style lang='less' scoped>
.form-style {
  margin: 20px 0;
}
.input-style:focus {
  outline: none;
  border-color: rgb(206, 212, 218);
  box-shadow: 0 0;
}
.input-style {
  width: 270px !important;
}
.btn {
  border: 1px solid #ccc;
}
</style>