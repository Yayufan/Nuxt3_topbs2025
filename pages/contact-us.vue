<template>
    <div>
        <main class="common-section">
            <h1 class="title">Contact Us</h1>
            <Breadcrumbs firstRoute="General Information" secoundRoute="Contact US"></Breadcrumbs>
        </main>
        
    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'

useSeoMeta({
    title: 'Contact Us - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Get in touch with the organizing committee of the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page provides contact information for inquiries, feedback, and assistance related to the conference.',
    keywords: 'Contact Us, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
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