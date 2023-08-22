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
    <div class="card">
        <div>
            {{ project.name }}
        </div>
        <div>
            {{ project.title }}
        </div>
        <div>
            {{ project.collaborators }}
        </div>
    </div>
</template>

<style scoped>
.card {
    display: flex;
    width: 33%;
}
</style>
