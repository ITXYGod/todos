<template>
    <footer class="footer">
        <!-- 
            这里用的是计算属性进行显示计数的
            也可以使用 farr.length 也是可以的
         -->
      <span class="todo-count">剩余<strong>{{ count }}</strong></span>
      <ul class="filters" @click="btnswitchFn">
        <li>
          <a :class="{selected: isSel === 'all'}" href="javascript:;" @click="isSel='all'">全部</a>
        </li>
        <li>
          <a :class="{selected: isSel === 'no'}" href="javascript:;" @click="isSel='no'">未完成</a>
        </li>
        <li>
          <a :class="{selected: isSel === 'yes'}" href="javascript:;" @click="isSel='yes'">已完成</a>
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
      },

      // 点谁谁高亮
      data() {
        return {
            // 全部: all, 已完成:yes, 未完成: no
            isSel: 'all'
        }
      },
      methods: {
        btnswitchFn() {
           this.$emit('changeType', this.isSel);
        }
      }
      
  }
  </script>