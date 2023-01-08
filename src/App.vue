<template>
<div class="w-5/12 mx-auto">
    <h1 class="text-4xl font-bold text-center text-indigo-600 mt-10">TodoList</h1>
    <form class="flex mb-8">
        <input type="text" v-model="newTask" class="px-4 py-2 text-white rounded-l-xl border border-indigo-800 outline-none text-black w-full mt-4" placeholder="Add the task...">
        <button class="bg-neutral-900 border-2 rounded-r-xl text-gray-200 border-indigo-800 px-4 py-2 mt-4" @click.prevent="addTask()">
			Add
        </button>
    </form>
	<ul class="">
        <li :key="task" v-for="(task, index) in tasks" class="flex justify-between items-center text-xl mb-4 text-black border rounded-md">
            <button @click="completedTask(task)" :class="task.completed ? 'text-green-600 line-through' : ''" class="px-4 py-2 w-full text-black flex justify-start">
                {{ index + 1 + '.' }} {{ task.title }}
            </button>
            <button @click="removeTask(index)" class="px-4 py-2 bg-red-600 rounded-xl text-base text-white">Remove</button>
        </li>
    </ul>
</div>
</template>

<script>

export default {
    name: 'App',
    components: {},
    data() {
        return {
            newTask: '',
            tasks: [{
                title: 'Practise with Tailwind',
                completed: false
            }]
        }
    },
    methods: {
        addTask() {
			if(this.newTask !== '') {
				this.tasks.push({
					title: this.newTask,
					completed: false
				});
			} else {
				alert('You should fill the gap!');
			}
            this.newTask = '';
        },
        completedTask(task) {
            task.completed = !task.completed;
        },
        removeTask(index) {
            this.tasks.splice(index, 1);
        }
    }
}
</script>

<style scoped>
input::placeholder {
    color: rgb(233, 233, 233);
}
</style>
