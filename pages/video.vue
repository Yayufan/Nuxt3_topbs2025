<template>
    <div>
        <main class="common-section">
            <h1 class="title">Video</h1>
            <Breadcrumbs firstRoute="General Information" secoundRoute="Video"></Breadcrumbs>
            <div class="content">
                <!-- <h1 class="">Page Under Construction</h1> -->
                <div class="video-banner">
            <img src="@/assets/img/video_banner.png" alt="">
        </div>
                <div class="video">
            <video src="@/assets/movie/promotionalVideo.mp4" controls></video>
        </div>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
</script>
<style lang="scss" scoped>
.common-section {
    width: $common-section-width;
    margin: $common-section-margin;
    font-family: $common-section-font-family;

    .title {
        margin-left: 7.4%;
        font-size: 2.5rem;
        color: $main-color;
    }
    .content {
        margin: 1rem auto;
        text-align: center;
        h1 {
            font-size: 2rem;
        }

        .video-banner {
        width: $common-section-width;
        margin: 5vw auto 0 auto;

        img {
            width: 100%;
        }
    }

        .video {
        width: $common-section-width;
        margin: $common-section-margin;

        video {
            width: 100%;
        }
    }
    }
}
</style>