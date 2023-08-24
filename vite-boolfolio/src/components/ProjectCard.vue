<script>

export default {
    name: 'ProjectCard',
    props: {
        project: {
            type: Object
        }
    }
}

</script>

<template>
    <div class="card">
        <div>
            <span>Name project:</span> {{ project.name }}
        </div>
        <div>
            <span>Title:</span> {{ project.title }}
        </div>
        <div>
            <span>Collaborators:</span> {{ project.collaborators }}
        </div>
        <div>
            <span>Finished:</span> {{ project.date_finished }}
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    display: inline-block;
    width: calc(100% / 4 - 10px);
    border: 2px solid greenyellow;
    margin: 10px;

    div {
        margin: 3px;

        span {
            font-weight: bold;
        }
    }
}
</style>
