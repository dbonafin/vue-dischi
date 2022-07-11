<template>

    <div class="album-card">
        <div class="album-image">
            <img :src="albumDetails.poster" :alt="albumDetails.title">
        </div>

        <div class="album-infos">

            <h3>{{albumDetails.title}}</h3>

            <h4>{{albumDetails.author}}</h4>
            <h4>{{albumDetails.year}}</h4>
                   <h4>{{albumDetails.genre}}</h4>

        </div>
    </div>

</template>

<script>

    export default {
        name: "AlbumCard",
        props: {albumDetails: Object}
    }

</script>
    
<style lang="scss">

    @import "../style/brand-colors.scss";

    div .album-card {
        width: 100%;
        height: 100%;
        padding: 10px 15px;
        .album-image {
            width: 110px;
            margin: 0 auto;
            height: 110px;
        }
        .album-infos {
            margin-top: 20px;
            text-align-last: center;
            h3 {
                text-align: center;
                text-transform: uppercase;
                margin-bottom: 20px;
                color: $album-name-color;
            }
            h4 {
                color: $album-infos-color;
            }
        }
    }

  
    
</style>