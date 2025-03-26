<template>
    <div class="banner-box">
        <img src="../../assets/img/banner.png" alt="">
    </div>
</template>
<style lang="scss" scoped>
     .banner-box {
        margin-top: 1rem;

        @media screen and (max-width: 850px) {
            margin: 6rem auto 0 auto !important; 

        }

        img {
            width: 100%;
            box-shadow: 0px 6px 10px 0px rgba(0, 0, 0, 0.5);
        }
    }
</style>