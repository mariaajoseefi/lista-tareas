<template>
    <div class="task-list">
        <input type="text" v-model="newTask" @keyup.enter="addTask" placeholder="Añadir tarea...">
        <ul>
            <li v-for="(task, index) in tasks" :key="index" class="task-item">
                {{ task }}
                <button @click="removeTask(index)" class="delete-button">Eliminar</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            tasks: [],
            newTask: ''
        };
    },
    methods: {
        addTask() {
            if (this.newTask.trim() === '') return;
            this.tasks.push(this.newTask);
            this.newTask = '';
        },
        removeTask(index) {
            this.tasks.splice(index, 1);
        }
    }
};
</script>

<style>
.task-list {
    font-family: Arial, sans-serif;
    padding: 20px;
    border: 1px solid #ddd;
    border-radius: 5px;
    max-width: 400px;
    margin: 0 auto;
}

.task-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ddd;
}

.delete-button {
    background-color: #f44336;
    color: white;
    border: none;
    padding: 5px 10px;
    border-radius: 3px;
    cursor: pointer;
}

.delete-button:hover {
    background-color: #d32f2f;
}
</style>
