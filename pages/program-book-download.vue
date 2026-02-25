<template>
    <div>
        <main class="common-section">
            <Banner />
            <Breadcrumbs firstRoute="Program" secoundRoute="Program Book"></Breadcrumbs>
            <div class="content">
                <Title title="Program Book" />
                <h1 v-if="!programBookFile || programBookFile.length === 0" class="">Page Under Construction</h1>

                <div v-if="programBookFile && programBookFile.length > 0" class="content">
                    <el-card class="file-card">
                        <div v-for="item in programBookFile" class="file-item">
                            <p>{{ item.name }}</p>
                            <div class="image-box">
                                <img :src="envMinio + item.coverThumbnailUrl" alt="">
                            </div>
                            <a class="download" :href="envMinio + item.path" target="_blank">Download</a>
                        </div>
                    </el-card>
                </div>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Title from '@/components/layout/Title.vue';
import Banner from '@/components/layout/Banner.vue';

const envMinio = useRuntimeConfig().public.minio

const programBookFile = ref<any>(null);
const getProgramBookFile = async () => {
    try {
        let res = await CSRrequest.get('/publish-file/programBook', {
            params: {
                type: "Program book"
            }
        })
        programBookFile.value = res.data;
        console.log(programBookFile.value);

    } catch (error) {
    }
}

onMounted(() => {
    getProgramBookFile();
});


</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;

    .title {
        margin-left: 7.4%;
        font-size: 2.5rem;
        color: $main-color;
    }

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
                justify-content: center;
                flex-wrap: wrap;
                gap: 0.5rem;
            }
        }

        .file-item {
            display: flex;
            flex-direction: column;
            width: 40%;
            aspect-ratio: 1 / 1;
            align-items: center;
            justify-content: center;
            margin: 1rem 0;
            padding: 1rem;
            // border: 1px solid #ccc;
            border-radius: 8px;
            gap: 1rem;

            @media screen and (max-width: 768px) {
                width: 70%;
            }

            @media screen and (max-width: 375px) {
                width: 90%;
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
                    // height: 100%;
                    aspect-ratio: 1 / 1;
                    // object-fit: cover;
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