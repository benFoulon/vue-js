<template>
    <div class="index">
        <h1>{{ title }}</h1>
    </div>
</template>

<script>
export default {
    name: 'TasksList',
    props: {
        title : String
    }
}
</script>