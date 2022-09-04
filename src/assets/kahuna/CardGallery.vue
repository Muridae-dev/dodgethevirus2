<template>
    <div class="card-gallery-container">
        <div class="card-container">
            <div class="card" v-for="card in cards" :key="card.name">
                <img :src="require(`./images/cards/${card.imgSrc}`)" :alt="card.name">
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'CardGallery',
        data() {
            return {
                cards:[
                    {
                        name: 'Butch',
                        cost: 2000,
                        description: 'Professional boxer',
                        imgSrc: 'butch.jpg'
                    },
                    {
                        name: 'Marsellus',
                        cost: 2000,
                        description: 'The boss',
                        imgSrc: 'marsellus.jpeg'
                    },
                    {
                        name: 'Mia',
                        cost: 2000,
                        description: 'Cool cat',
                        imgSrc: 'mia.jpeg'
                    },
                    {
                        name: 'Vincent',
                        cost: 2000,
                        description: 'Gets the job done',
                        imgSrc: 'vincent.webp'
                    },
                    {
                        name: 'The Wolf',
                        cost: 2000,
                        description: 'Cool cat',
                        imgSrc: 'wolfe.jpeg'
                    },
                ]
            }
        }
    }
</script>

<style lang="scss" scoped>
 .card-gallery-container {
    position:relative;
    width: 100%;
    height:40%;
    max-height:500px;
    background:blue;
 }
 .card-container {
    height:100%;
 }
 .card {
    float:left;
    height:100%;

 }

 img {
    height:90%;
    width:auto;
 }

 .card-text {
    
 }
</style>