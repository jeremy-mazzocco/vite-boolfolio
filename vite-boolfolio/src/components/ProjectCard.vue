<script>

export default {
    name: 'ProjectCard',
    props: {
        project: {
            type: Object
        }
    },
    methods: {
        showProjet(id) {
            this.$router.push('/projects/' + id);
        }
    },
    
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
        <button @click="showProjet(project.id)">Details</button>
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

    button {
        background-color: greenyellow;
        border-radius: 20px;
        border: none;
        padding: 5px;
        width: 4rem;
        margin: 10px 0px;
    }

    button:hover {
        cursor: pointer;
    }
}
</style>
