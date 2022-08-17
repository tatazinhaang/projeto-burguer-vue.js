<template>
    <div id="main-banner">
        <h1>Monte seu Hambúrguer</h1>
    </div>

</template>

<script>
export default {
    name: "Banner"
}
</script>

<style scoped>
     #main-banner {
        background-image: url('../../public/img/burguer.png');
        background-position: 0 -250px;
        background-size: cover;
        height: 500px;
        display: flex;
        align-items: center;
        justify-content: flex-start;
    }

    #main-banner h1 {
        color: #fff;
        text-align: center;
        font-size: 35px;
        padding: 20px 40px;
        background-color: rgba(34, 34, 34, 0.486);
    }

</style>