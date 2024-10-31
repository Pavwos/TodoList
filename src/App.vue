<template>
  <div id="app">
    <main  class="flex-grow flex flex-col items-center gap-4">
      <h1 class="text-5xl m-4">TodoList</h1>
      <TodoList/>
    </main>
    <footer class="flex flex-col items-center">
      <p>@pavwos © 2024</p>
    </footer>
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

<style scoped>
  #app{
    display: flex;
    flex-direction: column;
    min-height: 100vh;
    background-color: #F9FAFB;
    font-family: sans-serif;
  }
  h1{
    color: #22c55e;
    text-shadow: 0px 0px 5px #000;
    font-family: sans-serif;
    font-weight: bolder;
  }
  main{
    flex-grow: 1;
  }
  footer{
    margin-top: 15px;
    padding: 10px;
    background-color: #E5E7EB;
  }
</style>