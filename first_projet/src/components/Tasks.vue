<script>
export default {
    // name: "Tasks"
    props: {
        tasks: null,
    },
    methods: {
        completeTask(task) {
            this.$emit("completeTaskEvent",task);
        },

        deleteTask(index) {
            this.$emit("deleteTaskEvent",index);
        }

    }
};
</script>


<template>
    <div class="card mb-1 text-left">
        <ul class="list-group">
            <li class="list-group-item" v-for="(task, index) in tasks" :key="index">
                <div :class="task.completed ? 'completed' : ''">
                    {{ task.body }}
                </div>
                <div class="icons">
                    <i @click.prevent="completeTask(task)" class="fas fa-check-circle" style="color: green;"></i>
                    <i @click.prevent="deleteTask(index)" class="fas fa-trash-alt ml-3 ms-3" style="color: red;"></i>
                </div>
            </li>
        </ul>
    </div>
</template>

<style>
.completed{
    color: green;
    text-decoration: line-through;
}

.list-group-item{
    display: flex;
    /* color: green; */
    justify-content: space-between;
}
</style>