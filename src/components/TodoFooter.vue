<template>
    <footer class="footer">
        <!-- 
            这里用的是计算属性进行显示计数的
            也可以使用 farr.length 也是可以的
         -->
      <span class="todo-count">剩余<strong>{{ count }}</strong></span>
      <ul class="filters">
        <li>
          <a class="selected" href="javascript:;" >全部</a>
        </li>
        <li>
          <a href="javascript:;">未完成</a>
        </li>
        <li>
          <a href="javascript:;" >已完成</a>
        </li>
      </ul>
      <button class="clear-completed" >清除已完成</button>
    </footer>
  </template>
  
  <script>
  export default {
      props: ['farr'],
      // 使用计算属性来进行计数任务数量
      computed: {
         count() {
            return this.farr.length;
         }
      }
      
  }
  </script>