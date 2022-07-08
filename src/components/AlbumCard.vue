<template>

    <div class="album-card">
        <div class="album-image">
            immagine
        </div>

        <div class="album-infos">

            <h3>nome album</h3>

            <h4>artista</h4>
            <h4>anno release</h4>

        </div>
    </div>

</template>

<script>

    export default {
        name: "AlbumCard",
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
            background-color: lightcoral;
        }
        .album-infos {
            margin-top: 20px;
            text-align-last: center;
            h3 {
                margin-bottom: 20px;
                color: $album-name-color;
            }
            h4 {
                color: $album-infos-color;
            }
        }
    }

  
    
</style>