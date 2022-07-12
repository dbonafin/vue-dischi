<template>

    <div class="container">
        <!-- If loadingComplete is true - show all the albums -->
        <div class="row">

            <!-- For every object in the array print a card with all the infos -->
           <div v-for="(album,index) in filteredAlbums" :key="index" class="column">
                <AlbumCard :albumDetails="album"/>         
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
        props: {genreToShow: String},
        data() {
            return {
                url: "https://flynn.boolean.careers/exercises/api/array/music",
                albumsArray: [],
                albumsGenres: [],
            }
        },
        computed: {
            filteredAlbums () {
                if (this.genreToShow === '') {
                    return this.albumsArray;
                }

                return this.albumsArray.filter ((element) => {
                    element.genre === this.genreToShow;
                    console.log(element.genre)
                });
            }
        },
        mounted() {
            this.getAlbums()
        },
        methods: {
           getAlbums() {
                axios.get(this.url)
                .then((response) => {
                    // Fill the array with the datas inside the api
                    this.albumsArray = response.data.response;

                    this.albumsArray.forEach((album) => {
                        if (!this.albumsGenres.includes(album.genre)) {
                            this.albumsGenres.push(album.genre)
                        }
                    });

                    // Pass the genres info to the app vue
                    this.$emit("genresInfo", this.albumsGenres)
                });
           }
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