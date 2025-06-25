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

useSeoMeta({
    title: 'Video - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Watch the promotional video for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page features the conference video, providing insights into the event and its significance.',
    keywords: 'Video, Promotional Video, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS'
})
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