<template>

    <div class="container">
        <!-- If loadingComplete is true - show all the albums -->
        <div v-if="loadingComplete" class="row">

            <!-- For every object in the array print a card with all the infos -->
           <div v-for="(album,index) in filteredAlbums" :key="index" class="column">
                <AlbumCard :albumDetails="album" />          
           </div>

        </div>

        <!-- If loadingComplete is false - show the loader -->
        <div v-else>
            <div class="loader">
                <p class="loader-banner">loading</p>
                <img src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiPz4KPHN2ZyB3aWR0aD0iNzUycHQiIGhlaWdodD0iNzUycHQiIHZlcnNpb249IjEuMSIgdmlld0JveD0iMCAwIDc1MiA3NTIiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+CiA8ZyBmaWxsPSIjMTlkNzYxIiBmaWxsLXJ1bGU9ImV2ZW5vZGQiPgogIDxwYXRoIGQ9Im01MzMuMjcgMzIwLjU5aC0zMTQuNTRjLTMwLjU1NSAwLTU1LjQxNCAyNC44NTktNTUuNDE0IDU1LjQxNCAwIDMwLjU1OSAyNC44NTkgNTUuNDE0IDU1LjQxNCA1NS40MTRoMzE0LjU0YzMwLjU1NSAwIDU1LjQxNC0yNC44NTUgNTUuNDE0LTU1LjQxNCAwLTMwLjU1NS0yNC44NTktNTUuNDE0LTU1LjQxNC01NS40MTR6bTAgMTAyLjU0aC0zMTQuNTRjLTI1Ljk4NCAwLTQ3LjEyNS0yMS4xNDUtNDcuMTI1LTQ3LjEyNSAwLTI1Ljk4NCAyMS4xNDEtNDcuMTI1IDQ3LjEyNS00Ny4xMjVoMzE0LjU0YzI1Ljk4NCAwIDQ3LjEyNSAyMS4xNDUgNDcuMTI1IDQ3LjEyOSAwIDI1Ljk4NC0yMS4xNDEgNDcuMTIxLTQ3LjEyNSA0Ny4xMjF6Ii8+CiAgPHBhdGggZD0ibTM4Ny45NiAzMzkuMzVoLTE2OS4xNmMtMjAuMTYgMC0zNi42NTIgMTYuNDg4LTM2LjY1MiAzNi42NTIgMCAyMC4xNiAxNi40ODggMzYuNjU2IDM2LjY1MiAzNi42NTZoMTY5LjE2YzIwLjE2IDAgMzYuNjUyLTE2LjQ4OCAzNi42NTItMzYuNjU2IDAuMDAzOTA2LTIwLjE1Ni0xNi40OTItMzYuNjUyLTM2LjY1Mi0zNi42NTJ6Ii8+CiA8L2c+Cjwvc3ZnPgo=" alt="loading image">
            </div>
        </div>
    </div>

</template>

<script>

    import axios from "axios";
    import AlbumCard from './AlbumCard.vue';
    
    export default {
        name: "AlbumsList",
        components: { AlbumCard },
        data() {
            return {
                url: "https://flynn.boolean.careers/exercises/api/array/music",
                albumsArray: [],
                loadingComplete: false,
                genreSelection: ''
            }
        },
        methods: {
           getAlbums() {
                axios.get(this.url)
                .then((response) => {
                    // Fill the array with the datas inside the api
                    this.albumsArray = response.data.response;

                    // When the array got all the elements from the api, change the variable loadingComplete
                    this.loadingComplete = true;
                });
           }
        },
        mounted() {
            this.getAlbums()
        },
        computed: {
            filteredAlbums() {
                if (this.genreSelection = '') {
                    return this.albumsArray;
                }
                // return this.albumsArray.filter((album)=> {
                //     return this.album.name.includes(this.genreSelection);
                // })
            }
        }
    }

</script>

<style lang="scss" scoped>

    @import "../style/common.scss";
    @import "../style/brand-colors.scss";
    
   .container {
        height: calc(100vh - 140px);
        display: flex;
        align-items: center;
        .row {
            width: 1100px;
            height: 600px;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            .column {
                width: calc(100% / 5 - 40px);
                height: calc(100% / 2 - 20px);
                margin: 10px 20px;
                background-color: $bg-secondary-color;
            }
        }
        .loader {
            padding-left: 20px;
            width: 200px;
            margin: 0 auto;
            p {
                text-transform: uppercase;
                font-size: 40px;
                color: $green-elements;
                text-align: center;
            }
        }
    }

</style>