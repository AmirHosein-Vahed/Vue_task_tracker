<template>
    <form v-on:submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input v-model="text" type="text" name="text" placeholder="Add Task">
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input v-model="day" type="text" name="day" placeholder="Add Day & Time">
        </div>
        <div class="form-control-check">
            <label>Set Reminder</label>
            <input v-model="reminder" type="checkbox" name="reminder">
        </div>
        <input class="btn btn-block" type="submit" value="Save Task">
    </form>
</template>


<script>
export default {
    name: 'AddTask',
    data() {
        return {
            text: '',
            day: '',
            reminder: false
        }
    },
    methods: {
        onSubmit(e) {
            e.preventDefault()

            if (!this.text || !this.day) {
                alert("please add a task and day")
                return
            }

            const newTask = {
                id: Math.floor(Math.random() * 10000),
                text: this.text,
                day: this.day,
                reminder: this.reminder
            }
            // alert(newTask.id + "-" + newTask.text + "-" + newTask.day + "-" + newTask.reminder)

            this.text = ''
            this.day = ''
            this.reminder = false

            this.$emit('add-new-task', newTask)
            return
        }
    }
}
</script>

<style scoped>
.add-form {
    margin-bottom: 40px;
}
.form-control {
    margin: 20px 0px;
}
.form-control label {
    display: block;
}
.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}
.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.form-control-check label {
    flex: 12;
}
.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>