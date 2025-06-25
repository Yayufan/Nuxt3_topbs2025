<template>
    <div>
        <main class="common-section">
            <!-- <h1 class="title">Organizing Committee</h1> -->
            <Banner></Banner>
            <Breadcrumbs firstRoute="IOPBS & TOPBS" secoundRoute="Organizing Committee"></Breadcrumbs>
            <Title title="Committee"></Title>
            <div class="content">
                <div class="committee-list">
                    <div v-for="item in commiteeList" class="committee-item-box">
                        <div class="committee-item">
                            <h4 class="committee-job-title">{{ item.jobTitle }}</h4>
                            <div v-for="person in item.list" class="committee-person-list">
                                <p class="person-name"><span class="english-name">{{ person.englishName }}</span><span
                                        class="chinese-name">{{ person.chineseName }}</span></p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Banner from '@/components/layout/Banner.vue';
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Title from '@/components/layout/Title.vue';

useSeoMeta({
    title: 'Organizing Committee - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Meet the organizing committee of the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page provides details about the committee members, their roles, and contributions to the conference.',
    keywords: 'Organizing Committee, Committee Members, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

const commiteeList = reactive([
    {
        jobTitle: 'President',
        list: [{
            chineseName: '葉顯堂',
            englishName: 'Hsien-Tang Yeh',
        }
        ]
    }, {
        jobTitle: 'Organizer, 9th IOPBS',
        list: [{
            chineseName: '陳訓徹',
            englishName: 'Shin-Cheh Chen',
        }]
    }, {
        jobTitle: 'Honorary Chair, IOPBS',
        list: [{
            chineseName: '朴鎬用',
            englishName: 'Ho Yong Park',
        }]
    }
    
    , {
        jobTitle: 'Vice President',
        list: [{ 
            chineseName: '洪進昇',
            englishName: 'Chin-Sheng Hung',      
        }, {
             chineseName: '沈士哲',
            englishName: 'Shih-Che Shen',
        }
        ]
    }, {
        jobTitle: 'Secretary General',
        list: [{
            chineseName: '林敬翰',
            englishName: 'Joseph Lin',
        }]
    }, {
        jobTitle: 'Honorary President',
        list: [{
            chineseName: '鄭翠芬',
            englishName: 'Fiona Tsui-Fen Cheng',
        }]
    }, {
        jobTitle: 'Organizing Committee',
        list: [{
            chineseName: '張耀仁',
            englishName: 'Yao-Jen Chang',
        }, {
            chineseName: '陳柵君',
            englishName: 'Cha-Chun Chen',
        }, {
            chineseName: '陳達人',
            englishName: 'Dar-Ren Chen',
        }, {
            chineseName: '陳芳銘',
            englishName: 'Fang-Ming Chen',
        }, {
            chineseName: '陳錫根',
            englishName: 'Shyi-Gen Chen',
        }, {
            chineseName: '周旭桓',
            englishName: 'Hsu-Huan Chou',
        },  {
            chineseName: '謝家明',
            englishName: 'Chia-Ming Hsieh',
        },{
            chineseName: '黃其晟',
            englishName: 'Chi-Cheng Huang',
        },{
            chineseName: '郭文宏',
            englishName: 'Wen-Hung Kuo',
        },{
            chineseName: '賴鴻文',
            englishName: 'Hung-Wen Lai',
        },{
            chineseName: '廖國秀',
            englishName: 'Guo-Shiou Liao',
        },{
            chineseName: '劉良智',
            englishName: 'Liang-Chih Liu',
        },{
            chineseName: '歐陽賦',
            englishName: 'Fu Ou-Yang',
        },{
            chineseName: '曾信順',
            englishName: 'Hsin-Shun Tseng',
        },{
            chineseName: '王明暘',
            englishName: 'Ming-Yang Wang',
        },{
            chineseName: '巫承哲',
            englishName: 'Cheng-Che Wu',
        },{
            chineseName: '姚忠瑾',
            englishName: 'Chung-Chin Yao',
        },{
            chineseName: '游啓昌',
            englishName: 'Chi-Chang Yu',
        },{
            chineseName: '于家珩',
            englishName: 'Chia-Herng Yue',
        }
    ]
    }
    
    
    
    
  
])



</script>
<style lang="scss" scoped>
.common-section {
    // width: $common-section-width;
    margin: $common-section-margin;
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

        .committee-list {
            display: flex;
            flex-direction: column;
            gap: 3rem;

            .committee-item-box {
                .committee-item {
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    justify-content: center;
                    gap: 0.5rem;
                    .committee-job-title {
                        font-size: 1.5rem;
                        color: #B62D66;
                        margin-bottom: 1rem;
                    }

                    .committee-person-list {
                        flex-direction: column;
                        display: flex;
                        gap: 5.5rem;

                        .person-name {
                            font-size: 1.3rem;
                            display: flex;
                            justify-content: center;
                            align-items: center;
                            text-align: center;
                            gap: 0.5rem;

                        }
                    }
                }
            }
        }
    }
}
</style>