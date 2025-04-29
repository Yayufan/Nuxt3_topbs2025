<template>
    <div>
        <main class="common-section">
            <!-- <h1 class="title">President's Message</h1>
              -->
            <Banner />
            <Breadcrumbs firstRoute="TOPBS & IOPBS" secoundRoute="President's Message"></Breadcrumbs>
            <Title title="President's Message" class="title"></Title>

            <!-- <div class="card-section">
                <el-card v-for="(item, index) in presidentList" :key="item.name" class="president-card">
                    <div class="president-image-box">
                        <img :src="item.profilePhotoUrl" alt="President's Message" class="president-image" />
                    </div>
                    <h1 class="president-name">{{ item.name }}, <span class="president-country">{{
                        item.country }}</span></h1>
                    <p class="president-message">
                        {{ item.message }}
                    </p>
                    <div class="fade-mask">
                    </div>
                    <a class="see-more-btn" :href="`#president${index}`">See more</a>
                </el-card>
            </div>
            <el-divider></el-divider>
            <div class="main-section">
                <el-card v-for="(item, index) in presidentList" :id="`president${index}`"
                    class="president-message-card">
                    <p class="content">
                    <h1 class="president-name">{{ item.name }}, <span class="president-country">{{
                        item.country }}</span></h1>
                    <p class="president-message">
                        {{ item.message }}
                    </p>
                    <div class="president-sign-image-box">
                        <img src="../assets/img/Sign-HoYongPark.jpg" alt="">
                    </div>

                    </p>

                </el-card>
            </div> -->

        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue'
import Title from '@/components/layout/Title.vue'

import president1IPhoto from '../assets/img/HoYongPark.jpg'
import testPhoto from '../assets/img/team-img-01.png'

const isExpanded = ref(false)

const presidentList = reactive<any>([
    {
        name: 'Ho Yong Park',
        country: 'Korea',
        profilePhotoUrl: president1IPhoto,
        message: `When oncoplastic breast surgery first began in Europe about 30 years ago, it started from the need to improve the cosmetic outcomes of breast-conserving surgery, which often left unsatisfactory results in terms of breast shape. The goal was to enhance the aesthetic results while also ensuring good oncologic outcomes during surgery. This is considered the beginning of oncoplastic breast surgery.\n
    Since most of the initial developments took place in Europe, the surgical techniques were mainly developed for women with large breasts. Among these techniques, those based on reduction mammoplasty became the foundation, leading to the development of many other mammoplasty methods. This advancement improved the rate of breast-conserving surgery to about 70–80%. However, applying these techniques—originally designed for large breasts—to patients with small or moderate-sized breasts was not easy.\n
    As a result, many doctors in Asia began to discuss how to improve cosmetic outcomes of breast-conserving surgery for patients with small and moderate breast sizes. They realized that if there were no suitable techniques, then a proper oncoplastic reconstruction method specifically for Asian women with small to moderate-sized breasts was needed. This led to the beginning of the International Oncoplastic Breast Surgery Symposium (IOPBS).`
        },
    {
        name: 'John Doe',
        country: 'USA',
        profilePhotoUrl: testPhoto,
        message: 'Oncoplastic breast surgery has evolved significantly over the years, with advancements in techniques and technology. It is now a standard practice in many countries, providing patients with better options for breast conservation.'
    },
    {
        name: 'Jane Smith',
        country: 'UK',
        profilePhotoUrl: testPhoto,
        message: 'The future of oncoplastic breast surgery looks promising, with ongoing research and development aimed at improving patient outcomes and expanding the range of techniques available to surgeons.'
    }
])


</script>
<style lang="scss" scoped>
.common-section {
    // width: $common-section-width;
    margin: $common-section-margin;
    font-family: $common-section-font-family;

    .card-section {
        margin: 1rem auto;
        text-align: center;
        display: flex;
        justify-content: center;
        gap: 2rem;
        flex-wrap: wrap;

        .el-card {
            width: calc(100% / 3 - 6rem);
            box-shadow: 3px 4px 10px rgba(0, 0, 0, 0.7);

            :deep(.el-card__body) {
                aspect-ratio: 1/1.5;

                // background-color: #ccc;
                display: flex;
                flex-direction: column;
                justify-content: flex-start;
                align-items: center;
                position: relative;


                .president-image-box {
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    width: 60%;
                    aspect-ratio: 1/1;

                    overflow: hidden;
                    border-radius: 50%;
                    border: 1px solid #ccc;

                    img {
                        width: 100%;
                        height: 100%;
                        object-fit: cover;
                        object-position: top;
                    }
                }

                .president-name {
                    font-size: 2rem;
                    font-weight: bold;
                    margin-top: 1rem;
                }

                .president-country {
                    font-size: 1rem;
                    margin-top: 0.5rem;
                }

                .president-message {
                    display: -webkit-box;
                    margin-top: 1rem;
                    -webkit-line-clamp: 7;
                    line-clamp: 7;
                    line-height: 2rem;
                    -webkit-box-orient: vertical;
                    overflow: hidden;
                    text-overflow: ellipsis;
                    text-align: left;
                    white-space: pre-line;
                    transition: max-height 0.3s ease;
                }


                .fade-mask {
                    position: absolute;
                    bottom: 0;
                    left: 0;
                    right: 0;
                    height: 4rem;
                    background: linear-gradient(to bottom, rgba(255, 255, 255, 0.068), rgba(161, 155, 155, 0.562));
                    pointer-events: none;
                }

                .see-more-btn {
                    position: absolute;
                    bottom: 10px;
                    left: 50%;

                    transform: translateX(-50%);
                    background-color: rgba(255, 255, 255, 0.068);
                    border: none;
                    border-radius: 0.5rem;
                    padding: 0.3rem 0.8rem;
                    font-size: 0.875rem;
                    cursor: pointer;
                    z-index: 2;

                    &:hover {
                        color: white;
                        cursor: pointer;
                    }
                }
            }

        }

        @media screen and (min-width: 1920px) {
            .el-card {
                :deep(.el-card__body) {

                    .president-message {
                        -webkit-line-clamp: 13;
                        line-clamp: 13;

                    }

                }
            }

        }

        @media screen and (max-width: 1024px) {
            gap: 1rem;
            flex-direction: column;

            .el-card {
                width: 60%;
                margin: 0 auto;

                :deep(.el-card__body) {

                    .president-message {
                        -webkit-line-clamp: 10;
                        line-clamp: 10;
                    }

                }

            }

        }

        @media screen and (max-width: 486px) {

            .el-card {
                width: 80%;
                margin: 0 auto;

                :deep(.el-card__body) {

                    .president-message {
                        -webkit-line-clamp: 12;
                        line-clamp: 12;

                    }

                }
            }
        }

        @media screen and (max-width: 375px) {
            .el-card {
                width: 90%;
                margin: 0 auto;

                :deep(.el-card__body) {
                    .president-message {
                        -webkit-line-clamp: 8;
                        line-clamp: 8;
                    }
                }
            }

        }
    }

    .president-message-card {
        width: 85%;
        margin: 5rem auto;
        padding: 2rem;
        box-shadow: 3px 4px 10px rgba(0, 0, 0, 0.7);
        background-color: #fff;
        border-radius: 1rem;
        line-height: 2rem;
        text-align: left;
        color: #000;

        :deep(.el-card__body) {
            padding: 2rem;
            background-color: #fff;
            border-radius: 1rem;
            line-height: 2rem;
            text-align: left;
            color: #000;

            .president-name {
                font-size: 2rem;
                font-weight: bold;
                margin-top: 1rem;
            }


            .president-country {
                font-size: 1.5rem;
                margin-top: 0.5rem;
                font-weight: normal;
            }

            .president-message {
                font-size: 1.3rem;
                margin-top: 1rem;
                white-space: pre-line;
            }

            .president-sign-image-box {
                width: 10%;
                margin-left: auto;

                img {
                    width: 100%;
                    object-fit: cover;
                }

                // margin: 0 auto;
            }
        }
    }
}
</style>