<template>
    <ul>
        <li v-for="task in taskList" v-bind:key="task.id" v-bind:class="{done: task.taskCompleted}" >
            <input type="checkbox" v-model="task.taskCompleted" @click="changeTaskCompleted(task.id)" >
            {{task.text}}
            <button @click="deleteTask(task.id)">X</button>
        </li>
    </ul>
</template>

<script>

    export default ({
        props: ['taskList', 'changeTaskCompleted', 'deleteTask'],
        
        data() {
            return {
            }
        },
        methods: {
        },
    })
</script>

<style scoped>
    ul {
        list-style: none;
    }

    li {
        margin-bottom: 10px;
    }

    .done {
        text-decoration: line-through;
    }

</style>
