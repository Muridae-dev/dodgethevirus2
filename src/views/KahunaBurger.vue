<template>
    <section class="kahuna-container">
        <div class="logo-container">
            <img src="../assets/kahuna/mainlogo.webp" />
        </div>


        <div class="menu-container">
            <div class="burger-container">
                <img src="../assets/kahuna/burger1.jpeg" />
            </div>
            <article>
                "But I must explain to you how all this mistaken idea of denouncing pleasure and praising pain was born and I will give you a complete account of the system, and expound the actual teachings of the great explorer of the truth, the master-builder of human happiness. 
            </article>

            <article>
                But who has any right to find fault with a man who chooses to enjoy a pleasure that has no annoying consequences, or one who avoids a pain that produces no resultant pleasure?
            </article>
            <div class="burger-container">
                <img src="../assets/kahuna/burger2.jpeg" />
            </div>

            <div class="burger-container">
                <img src="../assets/kahuna/burger3.webp" />
            </div>
            <article style="width:200px">
                Nor again is there anyone who loves or pursues or desires to obtain pain of itself, because it is pain, but because occasionally circumstances occur in which toil and pain can procure him some great pleasure. To take a trivial example, which of us ever undertakes laborious physical exercise, except to obtain some advantage from it?
            </article>

            <article style="width:400px">
                On the other hand, we denounce with righteous indignation and dislike men who are so beguiled and demoralized by the charms of pleasure of the moment, so blinded by desire, that they cannot foresee the pain and trouble that are bound to ensue; and equal blame belongs to those who fail in their duty through weakness of will, which is the same as saying through shrinking from toil and pain. 
            </article>
            <div class="burger-container">
                <img src="../assets/kahuna/burger4.jpeg" />
            </div>
        </div>
    </section>
</template>

<script>
export default {
    
}
</script>

<style scoped>
    img {
        height:100%;
        width:auto;
    }

    article {
        height:300px;
        width:300px;
        padding-left:20px;
        padding-right:20px;

        background:black;
    }

    .kahuna-container {
        position:relative;
        width:100%;
        min-height:300%;
        height:auto;

        background:chartreuse;
    }

    .logo-container {
        position:relative;
        margin:auto;
        padding-top:20px;
        text-align: center;
        

        min-height:200px;
        height:5vh;
        width:auto;
    }

    .burger-container {
        height:300px;
        width:auto;
        position:relative;
    }

    .menu-container {
        width:80%;
        height:auto;

        position:relative;
        left:50%;
        padding-top:20px;
        transform:translateX(-50%);
        display:flex;
        flex-wrap: wrap;
        justify-content: center;
        row-gap: 20px;
    }
</style>