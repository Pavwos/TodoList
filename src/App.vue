<template>
  <div id="app" class="h-screen flex flex-col items-center justify-center">
    <h1 class="text-5xl m-4 font-bold">TodoList</h1>
    <TodoList/>
  </div>
</template>

<script>
  import TodoList from './components/TodoList.vue'
  export default {
    components:{
      TodoList
    }
  };
</script>