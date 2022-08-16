<template>
    <div class="static-background-container">
        <!----------------------------- MURKYS PROFILE ----------------------------->
        <div v-if="staticProfile == 'Murky'" class="static-background-container" style="background: linear-gradient(180deg, rgba(0,0,0,0) 0%, rgba(0,0,0,0) 50%, rgba(0,0,0,0.4) 100%);">
            <img :src="require('../assets/statics/static15.gif')" style="opacity:0.05"/>
            <img :src="require('../assets/statics/static3.gif')"/>
        </div>


        
    </div>





                <!--<div class="vhs-filter">
                <img :src="require('../assets/statics/static15.gif')" style="opacity:0.05" class="vhs-filter__r"/>
                <img :src="require('../assets/statics/static15.gif')" style="opacity:0.05" class="vhs-filter__g"/>
                <img :src="require('../assets/statics/static15.gif')" style="opacity:0.05" class="vhs-filter__b"/>

                <img :src="require('../assets/statics/static3.gif')" class="vhs-filter__r"/>
                <img :src="require('../assets/statics/static3.gif')" class="vhs-filter__g"/>
                <img :src="require('../assets/statics/static3.gif')" class="vhs-filter__b"/>
                </div>-->
</template>

<script>
export default {
    name: "StaticBackground",
    props: ["staticProfile", "background"],
    created() {
        console.log(this.background)
    }
}
</script>

<style lang="scss" scoped>
    .vhs-filter {
        overflow: hidden;
        position: relative;
        height:100%;
        width:100%;
        
        div { display: block; }
        
        &__r,
        &__g,
        &__b {
            left: 0;
            mix-blend-mode: screen;
            position: absolute;
            top: 0;
            z-index: 1;

            height:100%;
            background-image: url("../assets/murky/backgrounds/background3.jpeg");
            background-position: center;
            background-size:cover;
            width:100%;


            /*position:absolute;
            top:50%;
            left:50%;*/
        }
        
        &__r {
            filter: url('#r');
            transform: translate(1px, 2px);
        }
        &__g {
            filter: url('#g');
            transform: translate(-2px, -1px);
        }
        &__b {
            filter: url('#b');
            transform: translate(-0px, -0px);
        }

    }
</style>

<style scoped>
    .static-background-container {
        height:100%;
        width:100%;
        z-index:0;
        position:absolute;
        top:0;
        left:0;
    }

    img {
        height:100%;
        width:100%;
        position:absolute;
        opacity:0.1;
        
    }
</style>