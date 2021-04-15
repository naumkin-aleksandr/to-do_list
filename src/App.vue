<template>
    <div id="app">
        <h1>Список задач</h1>
        <input type="text" v-model="newTask">
        <button @click="addNewTask">Добавить</button>
        <List 
        :taskList="taskList" 
        :changeTaskCompleted="changeTaskCompleted"
        :deleteTask="deleteTask"
        />
    </div>
</template>

<script>
    import List from './components/List';

    export default {
        name: 'App',
        components: {
            List,
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
        }
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
