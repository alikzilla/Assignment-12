<template>
    <div>
        <input type="text" v-model="task" class="input" placeholder="Add Task">
        <p v-if="tasks.length == 0" class="condition">No task</p>
        <button @click="addTask()" class="add_button">Add Task</button>
        
        <div v-for="(taskItem, index) in tasks" :key="index" class="tasks">
            <div class="controls">
                 <input type="checkbox" v-model="taskItem.isChecked">
                <p :class="{ 'cross': taskItem.isChecked }"> {{ taskItem.task }} </p>
            </div>
            <button @click="deleteTask(index)" class="delete-button">Delete Task</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            task: '',
            tasks: [
               
            ]
        };
    },
    methods: {
        addTask() {
            this.tasks.push({ task: this.task, isChecked: false });
            this.task = '';
        },
        deleteTask(index) {
            this.tasks.splice(index, 1);
        }
    }
}
</script>

<style scoped>
.input {
    width: 100%;
    height: 50px;
    outline: none;
    font-size: 30px;
    padding: 5px 10px;
    margin-bottom: 10px;
}
.condition{
    color: red;
    font-size: 20px;
    margin-bottom: 10px;
}

.add_button {
    width: 100%;
    height: 50px;
    font-size: 30px;
    margin-bottom: 10px;
}

.tasks {
    width: 100%;
    height: 50px;
    background-color: white;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 25px;
    padding: 0 10px;
}
.controls{
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 5px;
}

.delete-button{
    background-color: rgb(206, 39, 39);
    border: none;
    border-radius: 5px;
    color: white;
    font-size: 15px;
    width: 100px;
    height: 30px;
    transition: 0.3s;
}
.delete-button:hover{
    background-color: red;
}
.cross {
    text-decoration: line-through;
}
</style>
