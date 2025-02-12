<template>
    <div class="breadcrumbs">
        <div class="temp-box"></div>
        <el-breadcrumb class="breadcrumb">
            <el-breadcrumb-item :to="{ path: '/' }"><img src="/img/home.svg" alt=""></el-breadcrumb-item>
            <el-breadcrumb-item>{{ props.firstRoute }}</el-breadcrumb-item>
            <el-breadcrumb-item>{{ props.secoundRoute }}</el-breadcrumb-item>
        </el-breadcrumb>
    </div>
</template>
<script lang="ts" setup>
    import { ArrowRight } from '@element-plus/icons-vue'

    const props = defineProps<{
        firstRoute: string,
        secoundRoute: string
    }>();


</script>
<style lang="scss" scoped>
.breadcrumbs {
    padding: 20px 0;
    max-width: 100vw;
    max-width: 100vw;
    display: flex;
    .breadcrumb {
        display: flex;
        line-height: 100%;
        font-size: 1rem;
        font-weight: normal;
        letter-spacing: 0.1rem;
        color: $main-content-color;
        margin-left: 9.5%;
       :deep(.is-link) {
            &:hover {
                color: $main-color;
            }
       }
       img {
        width: 1.4rem;
       }
    }
}
</style>