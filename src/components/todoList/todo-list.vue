<template>
  <!-- 任务列表 -->
  <div class="list-style">
    <ul v-for="item in listdata" :key="item.id" class="list-group">
      <li class="list-group-item d-flex justify-content-between align-items-center li-style">
        <div class="custom-control custom-checkbox">
          <input type="checkbox" class="custom-control-input checkbox-style checkbox-style" v-model="item.done" :id="item.id">
          <label :for="item.id" class="custom-control-label label-style" :class="item.done ? 'delete' :''">{{item.task}}</label>
        </div>
        <div>
          <span v-if="item.done" class="badge badge-success badge-pill">已完成</span>
          <span v-else class="badge badge-warning badge-pill">未完成</span>
          <a @click="removeItem(item.id)" class="a-style">删除</a>
        </div>
      </li>
    </ul>

  </div>
</template>

<script>
export default {
  name: 'todoList',
  emits: ['remove'],
  props: {
    listdata: {
      type: Array,
      required: true,
      default: []
    }
  },
  methods: {
    removeItem(id) {
      this.$emit('remove', id)
    }
  }
}
</script>

<style lang='less' scoped>
.list-group {
  width: 400px;
  // vertical-align: middle;
}
.list-style {
  font-size: 14px;
}
.delete {
  text-decoration: line-through;
  color: gray;
  font-style: italic;
}
a {
  cursor: pointer;
}

.badge {
  color: #fff;
}
.list-group {
  border-collapse: collapse;
}
.li-style {
  height: 50px;
}
.a-style {
  margin-left: 10px;
  font-size: 12px;
}
</style>