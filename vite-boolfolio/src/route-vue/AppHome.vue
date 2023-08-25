<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';

const apiURL = 'http://localhost:8000/api/v1';

export default {
    name: 'Projects',
    components: {
        ProjectCard
    },
    data: function () {
        return {
            projects: [],
            pages: [],
        }
    },
    methods: {
        changePage(pageURL) {
            axios.get(pageURL)
                .then(response => {

                    this.projects = response.data.projects.data;
                    this.pages = response.data.projects.links;
                    console.log(response.data.projects);
                })
                .catch(error => {
                    console.log(error);
                });
        }
    },
    mounted() {
        axios.get(apiURL + '/projects-page')
            .then(response => {

                this.projects = response.data.projects.data;
                this.pages = response.data.projects.links;
                console.log(response.data.projects);
            })
            .catch(error => {
                console.log(error);
            });
    }
}
</script>

<template>
    <div class="container">
        <ProjectCard v-for="project in projects" :key="project.id" :project="project" />
    </div>

    <div class="pages">
        <div v-for="(page, index) in pages" v-html="page.label" @click="changePage(page.url)">

        </div>
    </div>
</template>

<style lang="scss" scoped>
.container {
    text-align: center;

}

.pages {
    width: 70%;
    height: 50px;
    margin: auto;
    margin-top: 50px;
    text-align: center;
    display: flex;
    justify-content: space-around;

    div {
        width: 4%;
        font-size: 25px;
        line-height: 50px;
        background-color: greenyellow;
        border-radius: 50px;
    }

    div:hover {
        cursor: pointer;
    }
}
</style>
