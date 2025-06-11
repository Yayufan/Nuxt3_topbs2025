<template>
    <div>
        <main class="common-section">
            <!-- <h1 class="title">President's Message</h1>
              -->
            <Banner />
            <Breadcrumbs firstRoute="IOPBS & TOPBS" secoundRoute="President's Message"></Breadcrumbs>
            <Title title="President's Message" class="title"></Title>

            <div class="card-section">
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
                    <a class="see-more-btn" @click="toTarget(index)">See more</a>
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
                        <img :src="item.signPhotoUrl" alt="">
                    </div>

                    </p>

                </el-card>
            </div>

        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue'
import Title from '@/components/layout/Title.vue'

import president1Photo from '../assets/img/Ho-Yong-Park.jpg'
import president1Sign from '../assets/img/Sign-HoYongPark.jpg'

import president2Photo from '../assets/img/ChenShinCheh.jpg'
import president2Sign from '../assets/img/Sign-ChenShinCheh.jpg'

import president3Photo from '../assets/img/YeHsiangTang.jpg'
import president3Sign from '../assets/img/Sign-YeHsiangTang.jpg'

useSeoMeta({
    title: 'President\'s Message - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Read the messages from the presidents of the Taiwan Oncoplastic Breast Surgery Society and the International Oncoplastic Breast Surgery Symposium, welcoming attendees to the 9th IOPBS & TOPBS 2025 conference.',
    keywords: 'President\'s Message, IOPBS, TOPBS, 2025 Conference, Oncoplastic Breast Surgery'
})



import testPhoto from '../assets/img/team-img-01.png'

const isExpanded = ref(false)

const presidentList = reactive<any>([
    {
        name: 'Hsien-Tang Yeh',
        country: 'Taiwan',
        profilePhotoUrl: president3Photo,
        signPhotoUrl: president3Sign,
        message: `On behalf of the Taiwan Oncoplastic Breast Surgery Society (TOPBS), it is my great pleasure to welcome you to the 9th International Oncoplastic Breast Surgery Biannual Meeting and 2025 TOPBS Annual Meeting. This prestigious gathering will take place in the vibrant city of Taipei, at the Taipei International Convention Center, on November 15–16, 2025. We are truly excited to host you in Taiwan for this special joint event, where East meets West in the spirit of learning and friendship. \n
        This year’s meeting is guided by the theme “Sustainable Perfect Shape with Safety.” This theme highlights our dedication to achieving the best possible breast form (the perfect shape) for our patients while never compromising on oncologic safety. Our mission is to show that aesthetic excellence and patient safety can – and must – go hand in hand in oncoplastic breast surgery.\n
        As we convene for this conference, we focus on several core pillars that define our professional community and this event’s goals: \n
        Collaboration: Bringing together specialists across disciplines and borders to share knowledge and skills. Breast surgeons, plastic surgeons, oncologists, and nursing professionals will stand shoulder to shoulder, reflecting a true multidisciplinary approach. \n
        Innovation: Exploring new frontiers in oncoplastic techniques and breast care. We will discuss cutting-edge research, advanced surgical methods, and creative solutions that improve patient outcomes and quality of life. \n
        Safety: Ensuring every innovation is grounded in the highest standards of patient safety. From oncologic treatment efficacy to post-operative care, patient well-being remains our foremost priority. \n
        Shared Professional Growth: Learning and growing together as a global community. Through open dialogue, and case discussions, , we will nurture mutual growth, inspire each other, and strengthen the bonds within our international network of colleagues. \n
        Over the course of two exciting days, our program will feature a wide range of scientific sessions, panel discussions, and practical workshops. You can look forward to insightful lectures from pioneers in oncoplastic and reconstructive breast surgery, who will share the latest advancements in techniques such as oncoplastic breast-conserving surgery, breast reconstruction innovations, and patient-centered care approaches. Through these interactive sessions, we encourage everyone to ask questions, share their own experiences, and engage in meaningful conversations that will drive our field forward. \n
        Equally important to the scientific program is the opportunity to connect on a personal level. By the end of the meeting, I hope each of you will have not only gained new knowledge but also made new friends and future collaborators.\n
        In closing, I would like to express my sincere gratitude to each and every one of you for participating in this meeting. Your enthusiasm, knowledge, and willingness to share are what make this event possible and successful. It is our collective effort and passion that fuel the advancements in oncoplastic breast surgery. Thank you for joining us in this journey toward a “sustainable perfect shape with safety” for all our patients. Welcome to Taipei, and welcome to an exciting meeting filled with collaboration and growth. I look forward to greeting each of you personally and wish you a rewarding and enjoyable experience at the conference!\n
        Hsien-Tang Yeh, M.D.\n
        President, Taiwan Oncoplastic Breast Surgery Society `
    },

    {
        name: 'Shin-Cheh Chen',
        country: 'Taiwan',
        profilePhotoUrl: president2Photo,
        signPhotoUrl: president2Sign,
        message: `The rising incidence of breast cancer among Asian women year after year, along with a relatively higher rate among younger women compared to Western countries, demands greater attention and more effective treatment strategies. Thanks to a deeper understanding of disease mechanisms and advances in medical therapies, the surgical management of breast cancer has gradually shifted toward de-escalation — with breast-conserving surgery replacing mastectomy, sentinel lymph node biopsy replacing axillary lymph node dissection, and neoadjuvant chemotherapy replacing adjuvant chemotherapy.\n 
Driven by the desire to minimize surgical scarring and preserve the breast’s natural appearance, a variety of new surgical techniques have been developed, such as oncoplastic breast-conserving surgery, nipple-sparing mastectomy, and various implant-based and free flap reconstruction procedures. Ironically, these developments have made surgical approaches more complex and diverse.\n
In response to these changes, Taiwan established the Taiwan Oncoplastic Breast Surgery Society in 2017 and has since collaborated with Japan’s JOPBS and Korea’s KOPBS. Through initiatives focused on knowledge-sharing, education, and training, we strive to fulfill the mission of this annual meeting: “Sustainable Shape and Oncologic Safety”, while promoting global health equity, innovation, and research. 
Taipei’s pleasant November weather offers the perfect setting for travel. The city blends modernity with historical charm, featuring numerous heritage sites, world-renowned museums, and easily accessible mountain hot springs — all within just half an hour’s reach. We warmly welcome experts and scholars from Europe, America, Asia, and beyond to join us for this grand event — to exchange knowledge and enjoy a wonderful educational holiday in Taipei.\n
Shin-Cheh Chen, M.D.\n
 9th IOPBS Organizer, TOPBS Founding President `
    },

    {
        name: 'Ho Yong Park',
        country: 'Korea',
        profilePhotoUrl: president1Photo,
        signPhotoUrl: president1Sign,
        message: `Since most of the initial developments in oncoplastic breast surgery took place in Europe, the surgical techniques were mainly developed for women with large breasts. Among these techniques, those based on reduction mammoplasty became the foundation, leading to the development of many other mammoplasty methods. These advancements improved the rate of breast-conserving surgery to about 70–80%. However, applying these techniques—originally designed for large breasts—to patients with small or moderately sized breasts was not easy.\n
Many doctors in Asia began discussing how to improve the cosmetic outcomes of breast-conserving surgery for patients with small or moderate breast sizes. This led to the creation of the International Oncoplastic Breast Surgery Symposium (IOPBS). \n
We are very pleased that the 9th IOPBS will be held in Taiwan in 2025. \n
Since IOPBS started in Korea in 2007, a significant amount of time has passed. As IOPBS has been hosted in various Asian countries, it has helped us better understand the differences in breast cancer situations and treatment approaches—including surgery—between nations, and has promoted active knowledge exchange. \n
We also realized that in many Asian countries, the rate of mastectomy remains significantly higher than that of breast-conserving surgery, mainly due to the high number of advanced breast cancer cases. \n
Recognizing this shared reality, we hope to continue collaborating across borders to promote the early detection of breast cancer. Through this, we aim not only to save patients’ lives but also to preserve their breasts when possible, or to provide aesthetically satisfying reconstruction after mastectomy. We believe this collaborative effort will greatly benefit many women in Asia with small to moderate breast sizes. \n
Looking ahead, we hope that these continued efforts will lead to even more fruitful knowledge exchange through future IOPBS meetings. The 10th IOPBS is scheduled to be held in Korea in 2027, followed by the 11th IOPBS in Thailand in 2029. \n
We are also delighted that the 2025 Taiwan Oncoplastic Breast Surgery Symposium (TOPBS) will be jointly held with the 9th IOPBS. I would like to express my heartfelt gratitude to all the doctors and professionals in Taiwan who are involved in breast cancer surgery and treatment. I have no doubt that your dedication and efforts will significantly contribute to the advancement of breast cancer surgery and reconstruction in the future. \n
Ho Yong Park, M.D.\n
Honorary Chair, International Oncoplastic Breast Surgery Symposium 
        `
    },
])

const toTarget = (index: number) => {
    const targetId = `#president${index}`;
    const targetElement = document.querySelector(targetId) as HTMLElement;
    const header = document.querySelector('header'); // 假設你的頁面有固定的 <header>
    const headerHeight = header ? header.offsetHeight : 0;

    if (targetElement) {
        const targetPosition = targetElement.offsetTop - headerHeight;
        window.scrollTo({
            top: targetPosition,
            behavior: 'smooth',
        });
    }
}


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
                    -webkit-line-clamp: 6;
                    line-clamp: 6;
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
                        -webkit-line-clamp: 7;
                        line-clamp: 7;
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
                width: 15%;
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