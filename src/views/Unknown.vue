<template>
    <section class="main-container">
        <div class="outer-lines">

        </div>
    </section>
</template>

<script>
export default {

}
</script>

<style scoped>
    .main-container {
        width:100%;
        height:calc(100% - 72px);
        background:rgb(1, 15, 32);
        position:relative;
    }

    .outer-lines {
        width:85%;
        height:80%;
        border:2px solid rgb(255, 187, 0);

        position:absolute;
        top:50%;
        left:50%;
        transform:translate(-50%,-50%);
    }
</style>