<script>
import { ref } from 'vue';
import axios from 'axios';

export default {
    name: 'Projects',
    data: function () {
        return {
            projectes: [],
            // pages: []
        }
    },
    // methods: {

    //     loadPage(target) {

    //         if (target == null) return;

    //         this.loadRabbits(target);
    //     },
    //     loadRabbits(target) {
    //         axios.get(target)
    //             .then(response => {

    //                 const data = response.data;
    //                 console.log(data);

    //                 this.rabbits = data.rabbits.data;
    //                 this.pages = data.rabbits.links;
    //             })
    //             .catch(error => {
    //                 console.log(error);
    //             });
    //     }
    // },
    mounted() {

        axios.get('http://localhost/api/v1/projectsList')
            .then(response => {
                console.log(reponse.data);
            })
            .catch(error => {
                console.log(error);
            });
    }
}
</script>

<template>
    ciaooo
</template>

<style scoped></style>
