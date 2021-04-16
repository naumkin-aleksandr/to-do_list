<template>
    <label :class="{selected: taskCompleted}"> 
        <input type="checkbox" v-model="taskCompleted" @click="changeStateTask">
    </label>
</template>

<script>
    import {bus} from '../main';

    export default ({
        props: {
            taskCompleted: {
                type: Boolean,
            },
            id: {
                type: Number,
            }
        },
        methods: {
            changeStateTask: function() {
                bus.$emit('task-status', this.id)
            }
        }
    })
</script>


<style scoped>
    input {
        position: absolute;
        width: 1px;
        height: 1px;
        opacity: 0;
    }

    label {
        display: inline-block;
        width: 20px;
        height: 20px;
        border: 2px solid #000;
        border-radius: 50%;
        position: relative;
        cursor: pointer;
    }

    .selected::before {
        content: '';
        width: 10px;
        height: 10px;
        background: #000;
        border-radius: 50%;
        position: absolute;
        top: 5px;
        left: 5px;
    }
</style>
