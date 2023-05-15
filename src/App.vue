<template>
  <div>
    <div class="todoapp">
      <TodoHeader @create="addTaskFn" :arr="showArr"></TodoHeader>
      <TodoMain :arr="showArr" @deleteTask="deleteData"></TodoMain>
      <TodoFooter :farr="showArr" @changeType="typeFn" @clear="clearFn"></TodoFooter>
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
      // JSON.parse():反序列化：将JSON字符
      list: JSON.parse(localStorage.getItem('todoList')) || [],
      getSel: 'all'// 默认显示全部
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
    },
    typeFn(selected) {
       this.getSel = selected;
    },
    clearFn() {
       this.list = this.list.filter(obj => obj.isDone === false);
    }
  },
  //使用计算属性来进行展示数据
  computed: {
     showArr() {
        if (this.getSel === 'yes') {
          // filter(): 根据条件过滤数组元素,返回自己需要的数组元素
           return this.list.filter(obj => obj.isDone === true);
        } else if (this.getSel === 'no') {
           return this.list.filter(obj => obj.isDone === false);
        } else {
           return this.list;
        }
     }
  },

  // 数据缓存 侦听
  watch: {
     list: {
        deep: true,
        immediate: true,
        handler() {
          //JSON.stringify():序列化，将JS对象转换成JSON字符串
           localStorage.setItem('todoList', JSON.stringify(this.list))
        }
     }
  }
}
</script>

<style lang="scss" scoped></style>