<script>

export default {
    name: 'ProjectCard',
    props: {
        type: Object,
        required: true
    }

}

</script>

<template>
    <div>
        {{ project.name }}
    </div>
</template>

<style scoped></style>
