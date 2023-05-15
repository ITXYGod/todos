<template>
  <header class="header">
    <h1>todos</h1>
    <input id="toggle-all" class="toggle-all" type="checkbox" v-model="isAll">
    <label for="toggle-all"></label>
    <input class="new-todo" placeholder="输入任务名称-回车确认" autofocus @keydown.enter="downFn" v-model="task" />
  </header>
</template>
  
<script>
export default {
  data() {
    return {
      task: ""
    }
  },
  methods: {
    downFn() {
      // 子传父
      this.$emit('create', this.task);
      this.task = "";
    }
  },
  // 计算属性
  computed: {
    isAll: {
      set(checked) {
        this.arr.forEach(obj => obj.isDone = checked);
      },
      get() {
        //如果arr没有元素，那么every方法就没有数据可以遍历，那么就原地返回true
        // 所以这个时候，需要进行arr的内部数据的判断
        return this.arr.length !== 0 && this.arr.every(obj => obj.isDone === true);
      }
    }
  },
  props: ['arr']
}
</script>