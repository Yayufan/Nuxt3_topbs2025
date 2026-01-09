<template>
    <div>
        <main class="common-section">
            <Banner></Banner>
            <Breadcrumbs firstRoute="IOPBS & TOPBS" secoundRoute="Activity Photos"></Breadcrumbs>
            <Title title="Activity Photos" />
            <div class="gallery">
                <div v-for="(group, groupIndex) in photoList" :key="groupIndex" class="image-group">
                    <span v-for="(image, imgIndex) in group" :key="imgIndex" class="image-item">
                        <img :src="image" alt="Sponsor Image" loading="lazy" />
                    </span>
                </div>
            </div>
            <a class="link" href="https://drive.google.com/drive/folders/1Y0uqPjFFnsGTiWNb4CCg9WrUZvkaEewP?usp=sharing"
                target="_blank">See More</a>
        </main>

    </div>
</template>
<script setup lang="ts">
import Banner from '@/components/layout/Banner.vue'
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Title from '@/components/layout/Title.vue';

useSeoMeta({
    title: 'Activity Photos - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Explore the activity photos from the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page is currently under construction, but stay tuned for updates showcasing the highlights and memorable moments from the event.',
    keywords: 'Activity Photo , 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

const activityPhotoConfig = { key: 'diamond Sponsor', path: '@/assets/img/activity-photos/*.{png,jpg,svg,jpeg}' };

const cols = ref(4);
const screenWidth = ref(0);

onMounted(() => {
    generatePhotoList()
    screenWidth.value = window.innerWidth;
    window.addEventListener('resize', () => {
        screenWidth.value = window.innerWidth;

        if (screenWidth.value <= 425) {
            cols.value = 1;
        } else if (screenWidth.value <= 810) {
            cols.value = 2;
        } else if (screenWidth.value <= 1024) {
            cols.value = 3;
        } else {
            cols.value = 4;
        }
        generatePhotoList()
    });

});

const allGroupedSponsors = ref<any>({});
const photoList = ref<string[][]>([]);

const generatePhotoList = () => {
    photoList.value = [];
    // allGroupedSponsors.value = () => {
    let modules = import.meta.glob('@/assets/img/activity-photo/*.{png,JPG,jpg,svg}', { eager: true, query: '?url', import: 'default' });

    const galleryImages = ref<string[]>(Object.values(modules) as string[]);
    galleryImages.value.forEach((image, index) => {
        const groupIndex = Math.floor(index / cols.value);
        if (!photoList.value[groupIndex]) {
            photoList.value[groupIndex] = [];
        }
        photoList.value[groupIndex].push(image);
    });

};

// photoList.value =
// {
//     level: 'Platinum Sponsor',
//     sponsorLogos: allGroupedSponsors.value[1]['platinum Sponsor']
// }



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
        margin: 1rem auto;
        text-align: center;

        h1 {
            font-size: 2rem;
        }
    }

    .gallery {
        display: flex;
        flex-direction: column;
        gap: 1.5rem;
        margin: 2rem auto;
        width: 90%;

        .image-group {
            display: flex;
            flex-wrap: wrap;
            gap: 1rem;
            justify-content: center;

            .image-item {
                width: calc(100% / 4 - 1rem);
                box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
                border-radius: 8px;
                overflow: hidden;

                img {
                    width: 100%;
                    height: auto;
                    display: block;
                    transition: transform 0.3s ease;

                    &:hover {
                        transform: scale(1.05);
                    }
                }

                @media screen and (max-width: 1024) {
                    width: calc(100% / 3 - 1rem);
                }

                @media screen and (max-width: 810px) {
                    width: calc(100% / 2 - 1rem);
                }

                @media screen and (max-width: 425px) {
                    width: calc(100% / 1 - 1rem);
                }
            }
        }
    }



    .link {
        display: block;
        width: 10%;
        margin: 1rem auto;
        padding: 0.5rem 0.2rem;
        text-align: center;
        background-color: #DD6777;
        color: #fff;
        border: none;
        border-radius: 5px;

        &:hover {
            background-color: darken(#DD6777, 10%);
            transform: scaleX(1.05);
            cursor: pointer;
        }

        @media screen and (max-width: 768px) {
            width: 30%;
        }
    }



}
</style>