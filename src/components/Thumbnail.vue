<template>
    <div class="thumbnail-container" :style="{top: '5%', left: `${150*(index+1)}px`}" @click="windowedComponent.isActive=true">
        <img :src="require('../assets/' + windowedComponent.imgSrc)" /><br/>
        {{windowedComponent.name}}
    </div>
</template>

<script>
export default {
    name: "Thumbnail",
    props: ["windowedComponent", "index"]
}
</script>

<style>
    .thumbnail-container {
        height:auto;
        width:100px;
        text-align: center;
        position: absolute;
        background:rgba(0, 255, 157, 0.253);
        font-family:kaOne;
        color:black;
        transform:translateX(-50%);
    }

    img {
        height:auto;
        width:100px;
    }
</style>