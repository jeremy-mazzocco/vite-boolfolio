<script>
import axios from 'axios';

const apiURL = 'http://localhost:8000/api/v1';

export default {
    name: 'ProjectShow',
    data: function () {
        return {
            project: [],
        }
    },
    methods: {
        toHome() {
            this.$router.push('/');
        }
        ,
        show() {
            axios.get(apiURL + '/project/' + this.$route.params.id)
                .then(response => {

                    this.project = response.data.project;
                    console.log(this.project);

                })
                .catch(error => {
                    console.log(error);
                });
        }
    },
    // mounted() {

    // }
}

</script>

<template>
    <div>
        <span>Name project: </span> {{ project.name }}
    </div>
    <div>
        <span>Title: </span> {{ project.title }}
    </div>
    <div>
        <span>Collaborators: </span> {{ project.collaborators }}
    </div>
    <div>
        <span>Finished: </span> {{ project.date_finished }}
    </div>
    <div>
        <span>Used Technologies: </span><span v-for="technology in project.technologies">{{ technology.languages
        }}, </span>
    </div>
    <button @click="show()">Show</button>
    <button @click="toHome()">Home</button>
</template>

<style lang="scss" scoped>
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
</style>
