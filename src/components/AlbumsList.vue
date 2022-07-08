<template>

    <div class="container">
        <!-- If loadingComplete is true - show all the albums -->
        <div v-if="loadingComplete" class="row">

            <!-- For every object in the array print a card with all the infos -->
           <div v-for="(album,index) in albumsArray" :key="index" class="column">
                <AlbumCard :albumDetails="album" />          
           </div>

        </div>

        <!-- If loadingComplete is false - show the loader -->
        <div v-else>
            <div class="loader">
                loading zio
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
                loadingComplete: false
            }
        },
        methods: {
           getAlbums() {
                axios.get(this.url)
                .then((response) => {
                    this.albumsArray = response.data.response;

                    // When the array got all the elements from the api, change the variable loadingComplete
                    this.loadingComplete = true;
                });
           }
        },
        mounted() {
            this.getAlbums()
        },
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
    }

</style>