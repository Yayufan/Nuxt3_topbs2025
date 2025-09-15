<template>
    <main class="common-section">
        <Banner />
        <Breadcrumbs firstRoute="Program" secoundRoute="Program at a Glance"></Breadcrumbs>
        <Title title="Program at a Glance" class="title"></Title>

        <div class="content">
            <h1 class="">Page Under Construction</h1>
        </div>
        <!-- <div class="btn-section">
            <el-button :class="selectedDay === 'Day1' ? 'active' : ''" @click="selectedDayFunction('Day1')">Day1,
                Nov
                15</el-button>
            <el-button :class="selectedDay === 'Day2' ? 'active' : ''" @click="selectedDayFunction('Day2')">Day2,
                Nov
                16</el-button>
        </div>

        <div class="img-section">
            <img :src="imageUrl" alt="">
        </div> -->

    </main>
</template>
<script lang="ts" setup>
import Banner from '~/components/layout/Banner.vue';
import Breadcrumbs from '~/components/layout/Breadcrumbs.vue';
import Title from '~/components/layout/Title.vue';

useSeoMeta({
    title: 'Program at a Glance - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Explore the program at a glance for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page provides an overview of the conference schedule, including key sessions and events.',
    keywords: 'Program at a Glance, Conference Schedule, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

const selectedDay = ref('Day1');

const selectedDayFunction = (day: string) => {
    selectedDay.value = day;
    console.log(selectedDay.value);
    getProgramFile();
}

let imageUrl = ref<string>('');
const envMinio = useRuntimeConfig().public.minio



const getProgramFile = async () => {
    console.log('Fetching program file for:', selectedDay.value);
    try {
        let res = await CSRrequest.get('/publish-file/agenda', {
            params: {
                type: selectedDay.value
            }
        })
        imageUrl.value = ''; // Reset image URL before setting a new one
        console.log('Program file fetched successfully:', res);
        imageUrl.value = envMinio + res.data[0].path; // Assuming the response contains a 'path' field with the image URL
    } catch (error) {
        console.error('Error fetching program file:', error);
    }
}
onMounted(() => {
    getProgramFile();
});

</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;
    margin: $common-section-margin;

    .content {
        margin: 1rem auto;
        text-align: center;

        h1 {
            font-size: 2rem;
        }

    }

    .btn-section {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 2rem;
        gap: 2rem;

        .el-button {
            width: 20rem;
            border: 1px solid #DD6777;
            border-radius: 5px;

            &:hover {
                border: 1px solid #DD6777;
                background-color: #DD6777;
                color: #fff;
            }

            &.active {
                border: 1px solid #DD6777;
                background-color: #DD6777;
                color: #fff;
            }
        }
    }

    .img-section {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 2rem;

        img {
            width: 80%;
            height: auto;
            border-radius: 5px;
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
        }
    }
}
</style>