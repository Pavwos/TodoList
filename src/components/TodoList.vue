<template>
  <div id="TL">
    <main class="flex flex-col items-center gap-4">
      <input v-model="newTask" placeholder="Type your task..." @keyup.enter="addTask" class="border-2 border-black rounded-lg p-1" >
      <button @click="addTask" class="bg-green-600 text-slate-100 p-2 rounded-md w-20 font-bold">Add</button>
      <ul class="flex flex-col gap-2">
        <li v-for="(task, index) in tasks" :key="index" class="w-72 bg-slate-500 p-2 text-neutral-50 flex flex-row items-center justify-between gap-4 rounded-lg">
          {{ task }}
          <button @click="rmTask(index)" class="bg-red-500 text-slate-100 p-2 rounded-md w-20">Delete</button>
        </li>      
      </ul>
    </main>
    <footer class="flex flex-col items-center font-light">
      <p>@pavwos</p>
    </footer>
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
				this.tasks.push(this.newTask);
				this.newTask = "";
			}
		},
		rmTask(index) {
			this.tasks.splice(index, 1);
		}
	}
};
</script>