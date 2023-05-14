<template>
  <div>
    <div class="todoapp">
      <TodoHeader @create="addTaskFn"></TodoHeader>
      <TodoMain :arr="list" @deleteTask="deleteData"></TodoMain>
      <TodoFooter :farr="list"></TodoFooter>
    </div>
  </div>
</template>

<script>
import './styles/base.css';
import './styles/index.css';
// 引入组件
import TodoHeader from './components/TodoHeader.vue';
import TodoMain from './components/TodoMain.vue';
import TodoFooter from './components/TodoFooter.vue';
export default {
  data() {
    return {
      list: [
        { id: 100, name: "吃饭", isDone: true },
        { id: 201, name: "睡觉", isDone: false },
        { id: 103, name: "打豆豆", isDone: true },
      ]
    }
  },
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  },
  methods: {
    addTaskFn(task) { // 添加任务,接收TodoHeader组件的参数
      let id = this.list.length == 0 ? 100 : this.list[this.list.length - 1].id + 1;
      this.list.push({
        id: id,
        name: task,
        isDone: false
      })
    },
    deleteData(id) {
      let index =  this.list.findIndex(obj => obj.id === id)
       this.list.splice(index, 1);
    }
  }
}
</script>

<style lang="scss" scoped></style>