<template>

    <header>
        <div class="logo-div">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/1280px-Spotify_logo_without_text.svg.png" alt="spotify logo">
        </div>
    </header>

</template>

<script>


    export default {
        name: "PageHeader"
    }

</script>

<style lang="scss">

    @import "../style/common.scss";
    @import "../style/brand-colors.scss";

    header {
        background-color: $bg-secondary-color;
        .logo-div {
            padding: 10px 20px;
            width: 80px;
        }
    }
    
</style>