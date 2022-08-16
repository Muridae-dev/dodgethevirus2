<template>
    <div class="vhs-filter">
        <img :src="require('../assets/mascots/biggie.png')" class="vhs-filter__r"/>
        <img :src="require('../assets/mascots/biggie.png')" class="vhs-filter__g"/>
        <img :src="require('../assets/mascots/biggie.png')" class="vhs-filter__b"/>
    </div>
</template>

<script>
export default {
    props: ["imgSrc"]
}
</script>

<style lang="scss" scoped>
    .vhs-filter {
        overflow: hidden;
        position: relative;
        height:100%;
        width:auto;
        
        img { display: block; }
        
        &__r,
        &__g,
        &__b {
            left: 0;
            mix-blend-mode: screen;
            position: absolute;
            top: 0;
            z-index: 1;

            height:100%;
            width:auto;


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