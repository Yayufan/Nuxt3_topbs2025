<template>
    <div>
        <main class="common-section">
            <h1 class="title">President's Message</h1>
            <Breadcrumbs firstRoute="TOPBS & IOPBS" secoundRoute="President's Message"></Breadcrumbs>
            <div class="content">
                <h1 class="">Page Under Construction</h1>
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
    }
}
</style>