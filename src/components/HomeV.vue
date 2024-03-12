<template>
  <div class="container">
    <h1>Lista de Tareas</h1>
    <input type="text" v-model="task" @keyup.enter="addTask" placeholder="Agregar nueva tarea">
    <ul>
      <li v-for="(task, index) in tasks" :key="index" class="task-item">
        {{ task.title }} <button @click="removeTask(index)">Eliminar</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import axios from 'axios';

export default {
  name: 'App',
  setup() {
    const task = ref('');
    const tasks = ref([]);

    const fetchTasks = async () => {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/todos');
        tasks.value = response.data;
      } catch (error) {
        console.error('Error fetching tasks:', error);
      }
    };

    onMounted(fetchTasks);

    const addTask = () => {
      if (task.value.trim() !== '') {
        tasks.value.push({ title: task.value });
        task.value = '';
      }
    };

    const removeTask = (index) => {
      tasks.value.splice(index, 1);
    };

    return {
      task,
      tasks,
      addTask,
      removeTask
    };
  }
};
</script>

<style>
.container {
  max-width: 800px;
  margin: 0 auto 2em auto;
  padding: 2em;
  border-radius: 0.9em;
  box-shadow: inset 0 -3em 3em rgba(0,0,0,0.1),         
                    0.3em 0.3em 1em rgba(0,0,0,0.3);
}

h1{
  text-shadow: 0px 0px 5px #06048fb7;
  text-align: center;
}

input[type="text"] {
  background-color: #eee;
  border: none;
  padding: 1em;
  font-size: 1em;
  width: 95%;
  border-radius: 0.9em;
  box-shadow: 0 0.4rem #dfd9d9;
  cursor: pointer;
  margin-bottom: 1em;
}

ul {
  list-style-type: none;
  padding: 0;
}

.task-item {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: .9em;
  border-radius: 0.9em;
  margin-bottom: .5em;
  box-shadow: inset 0 -3em 3em rgba(0,0,0,0.1), 
                    0.3em 0.3em 1em rgba(0,0,0,0.3);
}

.task-item button {
  background: #06048fb7;
  color: white;
  font-family: inherit;
  padding: 0.45em;
  padding-left: 1em;
  font-size: 17px;
  font-weight: 500;
  border-radius: 0.9em;
  border: none;
  cursor: pointer;
  letter-spacing: 0.05em;
  display: flex;
  align-items: center;
  box-shadow: inset 0 0 1.6em -0.6em #714da6;
  overflow: hidden;
  position: relative;
  height: 2.8em;
  padding: 0 3em;
}

.task-item button:hover {
  background-color: #cc0000;
}
</style>
