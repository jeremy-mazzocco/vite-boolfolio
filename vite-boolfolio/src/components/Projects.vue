<script>
import { ref } from 'vue';
import axios from 'axios';
import ProjectCard from './ProjectCard.vue';

export default {
    name: 'Projects',
    components: {
        ProjectCard
    },
    data: function () {
        return {
            projects: [],

        }
    },
    mounted() {
        axios.get('http://localhost:8000/api/v1/projects-list')
            .then(response => {

                this.projects = response.data.projects
                console.log(response.data.projects);
            })
            .catch(error => {
                console.log(error);
            });
    }
}
</script>

<template>
    <h1>
        Projects List
    </h1>
    <div class="container">
        <ProjectCard v-for="project in projects" :key="project.id" :project="project" @click="showProject(project.id)" />
    </div>
</template>

<style lang="scss" scoped>
.container {
    text-align: center;
}
</style>
