<script>
import { ref } from 'vue';
import axios from 'axios';

export default {
    name: 'Projects',
    data: function () {
        return {
            projectes: [],

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
    <div>

    </div>
</template>

<style scoped></style>
