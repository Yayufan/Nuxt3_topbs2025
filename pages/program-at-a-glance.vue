<template>
    <div>
        <main class="common-section">
            <!-- <h1 class="title">Program at a Glance</h1>
            <Breadcrumbs firstRoute="Program" secoundRoute="Program at a Glance"></Breadcrumbs>
            <div class="content">
                <h1 class="">Page Under Construction</h1>
            </div> -->
            <Banner />
            <Breadcrumbs firstRoute="Program" secoundRoute="Program at a Glance"></Breadcrumbs>
            <Title title="Program at a Glance" class="title"></Title>

            <div class="btn-section">
                <el-button :class="selectedDay === 'day1'? 'active':''" @click="selectedDayFunction('day1')">Day1, Nov 15</el-button>
                <el-button :class="selectedDay === 'day2'? 'active':''" @click="selectedDayFunction('day2')">Day2, Nov 16</el-button>
            </div>

            <div class="img-section">
                <img v-if="selectedDay === 'day1'" src="../assets/img/program-day1.jpg" alt="">
                <img v-if="selectedDay === 'day2'" src="../assets/img/program-day2.jpg" alt="">
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue';
import Title from '@/components/layout/Title.vue';

useSeoMeta({
    title: 'Program at a Glance - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Explore the program at a glance for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page provides an overview of the conference schedule, including key sessions and events.',
    keywords: 'Program at a Glance, Conference Schedule, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

const selectedDay = ref('day1');
const selectedDayFunction = (day: string) => {
    selectedDay.value = day;
    console.log(selectedDay.value);
}



</script>
<style lang="scss" scoped>
.common-section {
    // width: $common-section-width;
    margin: $common-section-margin;
    font-family: $common-section-font-family;

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
            
            &:active {
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