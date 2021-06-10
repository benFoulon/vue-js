<template>
        <p v-if="completed" class="task--completed">{{title}}</p>
        <p v-else>{{title}}</p>
</template>

<script>
export default {
    name: 'Task',
    props: {
        id: Number,
        title : String
    }
}
</script>