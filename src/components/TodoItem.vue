<template>
    <li>
        <CheckboxTaskCompletion :id="task.id" :taskCompleted="task.taskCompleted" />
        <span :class="{done: task.taskCompleted}">{{task.text}}</span>  
        <BtnDeleteTask :id="task.id"/>
    </li>
</template>

<script>
    import CheckboxTaskCompletion from './CheckboxTaskCompletion';
    import BtnDeleteTask from './BtnDeleteTask';
    
    export default ({
        components: {
            CheckboxTaskCompletion,
            BtnDeleteTask,
        },
        props: {
            task: {
                type: Object,
            }
        },
    })
</script>

<style scoped>
    li {
        margin-bottom: 10px;
        list-style: none;
        display: flex;
        align-items: center;
    }

    span {
        margin: 0 10px;
    }

    .done {
        text-decoration: line-through;
    }
</style>
