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
    },
    mounted() {
            axios.get(apiURL + '/project/' + this.$route.params.id)
                .then(response => {

                    this.project = response.data.project;
                    console.log(this.project);

                })
                .catch(error => {
                    console.log(error);
                });
    }
}

</script>

<template>
    <div class="container">
        <div>
            <span class="title">Name project: </span> {{ project.name }}
        </div>
        <div>
            <span class="title">Title: </span> {{ project.title }}
        </div>
        <div>
            <span class="title">Collaborators: </span> {{ project.collaborators }}
        </div>
        <div>
            <span class="title">Finished: </span> {{ project.date_finished }}
        </div>
        <div>
            <span class="title">Used Technologies: </span>
            <span v-for="technology in project.technologies">{{
                technology.languages
            }}, </span>
        </div>
        <div>
            <span class="title">Type: </span> {{ project.type.stack }}
        </div>
        <button @click="toHome()">Home</button>
    </div>
</template>

<style lang="scss" scoped>
.container {

    width: 40%;
    margin: auto;
    text-align: center;
    margin-top: 50px;

    div {
        margin: 10px 0px;

        .title {
            font-size: 1.3rem;
            font-weight: bold;
        }
    }

    button {
        background-color: greenyellow;
        border-radius: 20px;
        border: none;
        padding: 5px;
        width: 4rem;
        margin: 10px 10px;
    }

    button:hover {
        cursor: pointer;
    }
}
</style>
