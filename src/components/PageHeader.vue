<template>

    <header>
        <div class="logo-div">
            <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/1/19/Spotify_logo_without_text.svg/1280px-Spotify_logo_without_text.svg.png" alt="spotify logo">
        </div>

        <div class="genre-nav">
            <h4>Select the genre that you want to listen</h4>

            <select v-model="selectText" @change="$emit('selectGenre', selectText)" id="genre-selection">
                <option value="all">All</option>
                <option value="rock">Rock</option>
                <option value="pop">Pop</option>
                <option value="jazz">Jazz</option>
                <option value="metal">Metal</option>
            </select>
        </div>
    </header>

</template>

<script>

    export default {
        name: "PageHeader",
        data() {
            return {
                selectText: 'all'
            }
        }
    }

</script>

<style lang="scss">

    @import "../style/common.scss";
    @import "../style/brand-colors.scss";

    header {
        display: flex;
        align-items: center;
        background-color: $bg-secondary-color;
        .logo-div {
            padding: 15px;
            margin-right: 60px;
            width: 80px;
        }
        .genre-nav {
            display: flex;
            align-items: center;
            h4 {
                color: $album-name-color;
            }
            #genre-selection {
            margin: 0 10px;
            padding: 2px 20px;
            font-weight: 700;
            text-align: center;
            border-radius: 5px;
            background-color: #19D861;
        }
        }
    }
    
</style>