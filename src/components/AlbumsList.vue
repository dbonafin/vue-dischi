<template>

    <div class="container">
        <div class="row">

           <div v-for="(album,index) in albumsArray" :key="index" class="column">
                <AlbumCard/>          
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
            }
        },
        methods: {
           getAlbums() {
                axios.get(this.url)
                .then((response) => {
                    this.albumsArray = response.data.response;
                    console.log(this.albumsArray);
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
            width: 1000px;
            height: 550px;
            margin: 0 auto;
            display: flex;
            flex-wrap: wrap;
            .column {
                width: calc(100% / 5 - 40px);
                height: calc(100% / 2 - 20px);
                margin: 10px 20px;
                background-color: $bg-secondary-color;
                // test 
                color: white;
            }
        }
    }

</style>