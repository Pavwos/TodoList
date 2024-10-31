<template>
  <div id="TL">
    <main class="flex flex-col items-center justify-between flex-wrap gap-4  w-full">
      <div id="inputField" class="flex flex-row gap-2">
        <input v-model="newTask" placeholder="Type your task..." @keyup.enter="addTask" class="border-2 border-black rounded-lg p-1" >
        <button id="add" @click="addTask" class="bg-green-600 text-slate-100 p-2 rounded-md w-20 font-bold">Add</button>
      </div>
      <div id="count">
        <p>Tasks: {{ tasks.length }}</p>
        <p>Checked: {{ completedTasks }}</p>
        <p>To-Do: {{ incompletedTasks }}</p>
      </div>
      <ul>
        <li v-for="(task, index) in tasks" :key="index" :class="{'line-through text-gray-500': task.completed}">
          {{ task.text }}
          <div id="btns">
            <button id="check" @click="check(index)" class="bg-green-500 text-slate-100 p-2 rounded-lg w-20 m-2">Check</button>
            <button id="del" @click="rmTask(index)" class="bg-red-500 text-slate-100 p-2 rounded-lg w-20">Delete</button>
          </div>
        </li>
      </ul>
    </main>
  </div>
</template>
<script>
export default {
	data() {
		return {
			newTask: '',
			tasks: [],
		};
	},
	methods: {
		addTask() {
			if (this.newTask.trim() !== '') {
				this.tasks.push({ text: this.newTask, completed: false});
				this.newTask = "";
			}
		},
		rmTask(index) {
			this.tasks.splice(index, 1);
		},
    check(index){
      this.tasks[index].completed = !this.tasks[index].completed
    }
	},
  computed: {
    completedTasks(){
      return this.tasks.filter(task => task.completed).length;
    },
    incompletedTasks(){
      return this.tasks.filter(task => !task.completed).length;
    }
  }
};
</script>
<style scoped>
  #count{
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
  }
  p{
    color: #374151;
  }
  button{
    transition: 0.5s;
    border: 1px solid #22c55e;
  }
  input{
    background-color: #cbd5e1;
    color: #000;
    outline: none;
    border: 1px solid #22c55e;
    transition: all 0.5s;
    padding: 10px 15px;
  }
  input:hover{
    border: 1px solid #22c55e;
    box-shadow: 1px 1px 10px #22c55e;
  }
  input::placeholder{
    color: #000
  }
  #add:hover{
    border: 1px solid #22c55e;
    box-shadow: 1px 1px 10px #22c55e;
  }
  ul{
    min-width: 50vh;
    max-width: 100vh;
    display: flex;
    flex-direction: column;
    width: 100%;
  }
  li{
    font-size: 18px;
    width: 100%;
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    justify-content: space-between;
    background-color: #d1ffe2;
    padding: 5px 10px;
    border: 2px solid #22c55e;
    border-radius: 5px;
    margin: 5px;
  }
</style>