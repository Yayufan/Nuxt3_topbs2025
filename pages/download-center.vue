<template>
    <div>
        <main class="common-section">
            <Banner />
            <!-- <h1 class="title">Download Center</h1> -->
            <Breadcrumbs firstRoute="IOPBS & TOPBS" secoundRoute="Download Center"></Breadcrumbs>
            <Title title="Download Center" class="title"></Title>
            <div class="content">
                <el-card class="file-card">
                    <div v-for="item in fileList" class="file-item">
                        <p>{{ item.name }}</p>
                        <div class="image-box">
                            <img :src="envMinio + item.coverThumbnailUrl" alt="">
                        </div>
                        <a class="download" :href="envMinio + item.path" target="_blank">Download</a>
                    </div>
                </el-card>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue';
import Title from '@/components/layout/Title.vue';

useSeoMeta({
    title: 'Download Center - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Access the Download Center for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page is currently under construction, but stay tuned for updates on downloadable resources, conference materials, and more.',
    keywords: 'Download Center, File Download, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

const envMinio = useRuntimeConfig().public.minio

const fileList = reactive<any>([]);

const getFileList = async () => {
    try {
        let res = await CSRrequest.get('/publish-file/downloadCenter/pagination', {
            params: {
                page: 1,
                size: 1000
            }
        })

        console.log('File list response:', res);
        Object.assign(fileList, res.data.records);
    } catch (error) {
        console.error('Error fetching file list:', error);
    }
}

const downloadFile = (filePath: string) => {

}

onMounted(() => {
    getFileList();
});



</script>
<style lang="scss" scoped>
.common-section {
    // width: $common-section-width;
    // margin: $common-section-margin;
    font-family: $common-section-font-family;

    .content {
        width: 80%;
        margin: 1rem auto;
        text-align: center;

        h1 {
            font-size: 2rem;
        }

        .file-card {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            align-items: center;
            width: 100%;
            padding: 1rem;
            background-color: #f9f9f9;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            :deep(.el-card__body) {
              display: flex;
                flex-wrap: wrap;
              gap: 0.5rem   ;
            }
        }

        .file-item {
            display: flex;
            flex-direction: column;
            width: calc(100%  / 4 - 3rem) ;
            aspect-ratio: 1 / 1;
            align-items: center;
            justify-content: space-between;
            margin: 1rem 0;
            padding: 1rem;
            // border: 1px solid #ccc;
            border-radius: 8px;
            gap: 1rem;

            @media screen and (max-width: 1024px) {
                width: calc(100% / 3 - 3rem);
            }

            @media screen and (max-width: 768px) {
                width: calc(100% / 2 - 3rem);
            }

            @media screen and (max-width: 480px) {
                width: calc(100% - 3rem);
            }

            p {
                font-size: 1.2rem;
                color: #333;
                margin-right: 1rem;
            }

            .image-box {
                width: 90%;

                img {
                    width: 100%;
                    height: 100%;
                    object-fit: cover;
                    border-radius: 8px;
                }
            }

            .download {
                display: inline-block;
                width: 100%;
                height: 40px;
                background-color: #DD6777;
                color: white;
                text-align: center;
                line-height: 40px;
                border-radius: 4px;
                text-decoration: none;
                transition: background-color 0.3s;

                &:hover {
                    // background-color: #0056b3;
                    transform: scale(1.05);
                }
            }
        }
    }
}
</style>