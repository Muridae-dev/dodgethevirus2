<template>
    <div class="static-background-container">
        <!----------------------------- MURKYS PROFILE ----------------------------->
        <div v-if="staticProfile == 'Murky'">
            <img :src="require('../assets/statics/static15.gif')" style="opacity:0.05"/>
            <img :src="require('../assets/statics/static3.gif')" />
        </div>
    </div>    
</template>

<script>
export default {
    name: "StaticBackground",
    props: ["staticProfile"]
}
</script>

<style scoped>
    .static-background-container {
        height:100%;
        width:100%;
        z-index:0;
        position:absolute;
        background: linear-gradient(180deg, rgba(0,0,0,0) 0%, rgba(0,0,0,0) 50%, rgba(0,0,0,0.4) 100%);
    }

    img {
        height:100%;
        width:100%;
        position:absolute;
        opacity:0.2;
        
    }
</style>