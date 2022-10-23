<template>
    <div v-on:dblclick="toggleReminder()" v-bind:class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{ task.text }}<i v-on:click="$emit('delete-task', task.id)" class="fas fa-times"></i></h3>
        <p>{{ task.day }}</p>
    </div>
</template>


<script>
export default {
    name: 'Task',
    props: {
        task: Object
    },
    methods: {
        toggleReminder() {
            this.task.reminder = !this.task.reminder;
        }
    }
}
</script>


<style scoped>
.fas {
    color: red;
}
.task {
    background: #faeeee;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}

.task.reminder {
    border-left: 5px solid green;
}

.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>