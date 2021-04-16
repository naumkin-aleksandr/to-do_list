<template>
    <div id="app">
        <h1>Список задач</h1>
        <input  type="text" v-model="newTask" >
        <button @click="addNewTask">Добавить</button>
        <ul>
            <TodoItem 
                v-for="task in taskList" 
                :key="task.id"
                :task="task"
            />                
        </ul>
    </div>
</template>

<script>
    import TodoItem from './components/TodoItem';
    import {bus} from './main';

    export default {
        name: 'App',
        components: {
            TodoItem,
        },
        data() {
            return {
                newTask: '',
                taskList: [
                    {id: 1, text: 'Изучить JavaScript', taskCompleted: true,},
                    {id: 2, text: 'Изучить Vue', taskCompleted: false},
                    {id: 3, text: 'Сделить To-do List', taskCompleted: false},
                ]
            }
        },
        methods: {
            addNewTask: function() {
                if(this.newTask.trim().length === 0) return;
                const id = Date.now()
                const text = this.newTask;
                const taskCompleted = false;
                this.taskList.push({id, text, taskCompleted});
                this.newTask = '';
            }, 
            changeTaskCompleted: function(id) {
                this.taskList.map(item => item.id === id ? item.taskCompleted = !item.taskCompleted: item);
            },
            deleteTask: function(id) {
                this.taskList = this.taskList.filter(item => item.id !== id);
            }
        },
        created() {
            bus.$on('delete-task', this.deleteTask);
            bus.$on('task-status', this.changeTaskCompleted)
        },
    }
</script>

<style >
    #app {
        width: 500px;
        margin: 50px;
        padding: 20px;
        font-family: Avenir, Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: #2c3e50;
        border: 2px solid #2c3e50;
    }
</style>
