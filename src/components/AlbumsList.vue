<template>

    <div class="container">
        <div class="row">
           
           <div class="column">
                <div class="album-card">
                    <p>lorem impsppsspps</p>
                </div>            
           </div>
           <div class="column">
                <div class="album-card">

                </div>            
           </div>
           <div class="column">
                <div class="album-card">

                </div>            
           </div>
           <div class="column">
                <div class="album-card">

                </div>            
           </div>
           <div class="column">
                <div class="album-card">

                </div>            
           </div>
           <div class="column">
                <div class="album-card">

                </div>            
           </div>
           <div class="column">
                <div class="album-card">

                </div>            
           </div>

        </div>
    </div>

</template>

<script>

    export default {
        name: "AlbumsList"
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