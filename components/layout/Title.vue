<template>
     <div class="title-section">
                <p class="title">
                    {{ props.title }}
                </p>
            </div>
</template>
<script lang="ts" setup>
    const props = defineProps<{
        title: string
    }>()
</script>
<style lang="scss" scoped>
 .title-section {
        margin-top: 1rem;
        text-align: center;
        position: relative;

        .title {
            font-size: 2.7rem;
            font-weight: 600;
        }

    }
</style>