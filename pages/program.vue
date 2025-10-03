<template>
    <div>
        <main class="common-section">
            <!-- <h1 class="title">Program at a Glance</h1>
            <Breadcrumbs firstRoute="Program" secoundRoute="Program at a Glance"></Breadcrumbs>
            <div class="content">
                <h1 class="">Page Under Construction</h1>
            </div> -->
            <Banner />
            <Breadcrumbs firstRoute="Program" secoundRoute="Program"></Breadcrumbs>
            <Title title="Program" class="title"></Title>

            <div class="btn-section">
                <el-button :class="selectedDay === 'Day1' ? 'active' : ''" @click="selectedDayFunction('Day1')">Day1,
                    Nov
                    15</el-button>
                <el-button :class="selectedDay === 'Day2' ? 'active' : ''" @click="selectedDayFunction('Day2')">Day2,
                    Nov
                    16</el-button>
            </div>

            <div class="btn-room-section">
                <el-button :class="selectRoom === '101' ? 'active' : ''" class="room1-btn"
                    @click="selectRoomFunction('101')">101</el-button>
                <el-button :class="selectRoom === '102' ? 'active' : ''" class="room2-btn"
                    @click="selectRoomFunction('102')">102</el-button>
                <el-button :class="selectRoom === '103' ? 'active' : ''" class="room3-btn"
                    @click="selectRoomFunction('103')">103</el-button>
                <!-- <el-button :class="selectRoom === '103' ? 'active' : ''" class="room3-btn"
                    @click="selectRoomFunction('103')">103</el-button> -->
            </div>

            <div class="img-section">
                <!-- <img v-if="selectedDay === 'day1'" src="../assets/img/program-day1.jpg" alt="">
                <img v-if="selectedDay === 'day2'" src="../assets/img/program-day2.jpg" alt=""> -->
                <img :src="imageUrl" alt="">
            </div>
            <div class="warning">
                <p v-if="selectRoom === '103'">*Meet Professor - Expert Video Show (Limited Seats(20) - Pre-Registration
                    Required)</p>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue';
import Title from '@/components/layout/Title.vue';

useSeoMeta({
    title: 'Program - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Explore the program for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page provides an overview of the conference schedule, including key sessions and events.',
    keywords: 'Program, Conference Schedule, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

const selectedDay = ref('Day1');
const selectRoom = ref('101');


const selectedDayFunction = (day: string) => {
    selectedDay.value = day;
    console.log(selectedDay.value);
    getProgramFile();
}

const selectRoomFunction = (room: string) => {
    selectRoom.value = room;
    getProgramFile();
}

// const type = ref('Day1-101');
const agendaFile = ref<any>();
let imageUrl = ref<string>('');
const envMinio = useRuntimeConfig().public.minio



const getProgramFile = async () => {
    console.log('Fetching program file for:', `${selectedDay.value}-${selectRoom.value}`);
    try {
        let res = await CSRrequest.get('/publish-file/agenda', {
            params: {
                type: `${selectedDay.value}-${selectRoom.value}`
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

            &.active {
                border: 1px solid #DD6777;
                background-color: #DD6777;
                color: #fff;
            }
        }
    }

    .btn-room-section {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 2rem;

        .el-button {
            width: 10rem;
            border: 1px solid #DD6777;
            // color: #fff;
            border-radius: 0px;
            margin: 0;

            &:hover {
                border: 1px solid #DD6777;
                // background-color: #DD6777;
                background: linear-gradient(to right, #E28A90, #A4557D);
                color: #fff;
            }

            &.active {
                border: 1px solid #DD6777;
                background-color: #DD6777;
                background: linear-gradient(to left, #E28A90, #A4557D);
                color: #fff;
            }

            &.room1-btn {
                border-radius: 10px 0px 0px 0px;
                // background: linear-gradient(to left, #E28A90, #A4557D);
            }

            &.room2-btn {
                border-radius: 0px;
                border-radius: 0px 0px 0px 0px;
                // background: linear-gradient(to left, #A4557D, #E28A90);
            }

            &.room3-btn {
                border-radius: 0px 10px 0px 0px;
                // background: linear-gradient(to left, #E28A90, #A4557D);
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
            box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);       }
    }

    .warning {
        width: 100%;
        display: flex;
        justify-content: center;
        margin-top: 1rem;

        p {
            color: #EB7574;
            font-weight: bold;
        }
    }
}
</style>