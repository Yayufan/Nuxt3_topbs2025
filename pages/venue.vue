<template>
    <div>
        <main class="common-section">
            <Banner></Banner>
            <Title title="Venue"></Title>
            <Breadcrumbs firstRoute="IOPBS & TOPBS" secoundRoute="Venue"></Breadcrumbs>
            <div class="content">
                <img src="@/assets/img/250916-Venue.png" alt="">
                <a href="/files/250916_Venue.pdf" target="_blank" class="download">Download Venue</a>
            </div>

        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Title from '@/components/layout/Title.vue';
import Banner from '@/components/layout/Banner.vue';

useSeoMeta({
    title: 'Venue - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Discover the venue details for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page is currently under construction, but stay tuned for updates on the event location, facilities, and more.',
    keywords: 'Venue, Location, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})
</script>
<style lang="scss" scoped>
.common-section {
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
        width: 80%;

        h1 {
            font-size: 2rem;
        }

        img {
            width: 100%;
            margin-top: 2rem;
        }

        .download {
            display: inline-block;
            margin-top: 1rem;
            padding: 0.5rem 1rem;
            background-color: #DD6777;
            color: white;
            text-decoration: none;
            border-radius: 5px;
            transition: background-color 0.3s;

            &:hover {
                background-color: darken(#DD6777, 10%);
                transform: scaleX(1.05);
            }
        }
    }
}
</style>