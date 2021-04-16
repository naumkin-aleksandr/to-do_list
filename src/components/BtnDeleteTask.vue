<template>
    <button v-on:click="deleteTask" >X</button>
</template>

<script>
import {bus} from '../main';

export default {
    props: {
        id: {
            type: Number,
        }
    },
    methods: {
        deleteTask: function() {
            bus.$emit('delete-task', this.id);
        }
    }
}
</script>

<style scoped>
    button {
        padding: 2px 5px;
        font-weight: 700;
        color: #fff;
        background: #000;
        border: 1px solid #000;
        border-radius: 3px;
        cursor: pointer;
        transition: background .2s, color .2s;
    }

    button:hover {
        background: #fff;
        color: #000;
    }
</style>