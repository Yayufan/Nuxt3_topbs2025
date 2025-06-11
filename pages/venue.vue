<template>
    <div>
        <main class="common-section">
            <h1 class="title">Venue</h1>
            <Breadcrumbs firstRoute="IOPBS & TOPBS" secoundRoute="Venue"></Breadcrumbs>
            <div class="content">
                <h1 class="">Page Under Construction</h1>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'

useSeoMeta({
    title: 'Venue - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Discover the venue details for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page is currently under construction, but stay tuned for updates on the event location, facilities, and more.',
    keywords: 'Venue, Location, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
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
    }
}
</style>