<template>
    <div>
        <main class="common-section">
            <h1 class="title">List of Sponsors</h1>
            <Breadcrumbs firstRoute="Sponsorship & Exhibition" secoundRoute="List of Sponsors"></Breadcrumbs>
            <div class="content">
                <h1 class="">Page Under Construction</h1>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'

useSeoMeta({
    title: 'List of Sponsors - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Explore the list of sponsors for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page is currently under construction, but stay tuned for updates showcasing the esteemed sponsors who support and contribute to the success of the conference.',
    keywords: 'List Of Sponsors, Sponsors, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
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