<template>
  <div>
     <div class="todoapp">
         <TodoHeader></TodoHeader>
         <TodoMain></TodoMain>
         <TodoFooter></TodoFooter>
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
  components: {
    TodoHeader,
    TodoMain,
    TodoFooter
  }
}
</script>

<style lang="scss" scoped></style>