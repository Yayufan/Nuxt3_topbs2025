<!--  -->
<template>

    <!-- <section> -->
        <div class="newsBox">

            <!-- 最新消息標題盒子 -->
            <div class="title-box">
                <div class="title-text-box">
                    <div class="title-image-box">
                        <img class="home-banner-bak" src="../../assets/img/EmojiObjectsOutlined.svg">
                    </div>
                    <h1 class="title">News</h1>
                </div>
                <nuxt-link class="more-link" to="/news">
                    more<el-icon>
                        <ElIconArrowRight />
                    </el-icon>
                </nuxt-link>
            </div>

            <!-- 最新消息內容盒子  -->
            <!-- 以下為首頁頁面HTML  -->
            <div class="NewsOuterBox" style="position: relative;">

                <ul class="NewsInnerBox">

                    <!-- li有多個,所以使用v-for  -->
                    <li class="NewsItem" v-for="(item, index) in newsList.records" :key="item.newsURL" @click="headToNews(item.articleId)">
                        <a :href="item.newsURL">
                            <p class="NewsItemTitle">{{ item.title }}</p>
                            <p class="NewsItemDate">{{ item.announcementDate }}</p>
                        </a>
                    </li>


                </ul>

                <!-- 
                    分頁插件 total為總資料數(這邊設置20筆),  default-page-size代表每頁顯示資料(預設為10筆,這邊設置為5筆) 
                    current-page當前頁數,官方建議使用v-model與current-page去與自己設定的變量做綁定,
                -->
                <!-- <div class="example-pagination-block">
                    <el-pagination layout="prev, pager, next" :total="15" :default-page-size="5"
                        v-model:current-page="currentPage" />
                </div> -->


            </div>

        </div>
    <!-- </section> -->

</template>


<script setup lang='ts'>

//import { Search,Document } from '@element-plus/icons-vue'

const router = useRouter()

let newsList = reactive<any>([])

const getNewsList = async () => {
    console.log(currentPage.value)
    let res = await CSRrequest.get('/article/pagination', {
        params: {
            page: currentPage.value,
            size: 3
        }
    })

    Object.assign(newsList, res.data)
    console.log("獲取的最新消息列表", newsList.records.length)
    let total = newsList.records.length
    for(let i = 0; i < 3-total; i++){
        console.log('length: ',newsList.records.length)
        console.log('total',3-newsList.records.length)
        newsList.records.push({
            title: "Coming soon",
            announcementDate: "無最新消息",
            newsURL: "#"
        })
    }
    console.log("獲取的最新消息列表", res.data)
}

const headToNews = (id: number) => {
    console.log("點擊了最新消息", id)
    router.push('/news-item/' + id)
}


onMounted(() => {
    getNewsList()
})



//測試數據'


// let newsList = reactive([{
//     newsURL: "component/news/news20240321.html",
//     newsDate: "2024/03/22",
//     newsType: "診所公告",
//     newTitle: "查詢功能開放"
// }, {
//     newsURL: "component/news/news20240314.html",
//     newsDate: "2024/03/14",
//     newsType: "診所公告",
//     newTitle: "後台功能新增"
// }, {
//     newsURL: "component/news/news20240305.html",
//     newsDate: "2024/03/05",
//     newsType: "診所公告",
//     newTitle: "疫苗施打服務"
// }, {
//     newsURL: "component/news/news20240105.html",
//     newsDate: "2024/01/05",
//     newsType: "診所公告",
//     newTitle: "休診公告"
// }, {
//     newsURL: "component/news/news20231115.html",
//     newsDate: "2023/11/15",
//     newsType: "診所公告",
//     newTitle: "診所網站開始運行"
// },
// ])


//設定currentPage當前頁數
let currentPage = ref(1)

//監聽當前頁數的變化,如果有更動就call API 獲取數組數據
//之後將資料更新到newsList 響應式的最新消息列表中
// watch(currentPage, (value, oldValue) => {

//     console.log("原本的newsList", newsList)

//     //先創建兩個假數據,用於展示效果
//     let oldOneList = [{
//         newsURL: "component/news/news20240321.html",
//         newsDate: "2024/03/22",
//         newsType: "診所公告",
//         newTitle: "查詢功能開放"
//     }, {
//         newsURL: "component/news/news20240314.html",
//         newsDate: "2024/03/14",
//         newsType: "診所公告",
//         newTitle: "後台功能新增"
//     }, {
//         newsURL: "component/news/news20240305.html",
//         newsDate: "2024/03/05",
//         newsType: "診所公告",
//         newTitle: "疫苗施打服務"
//     }, {
//         newsURL: "component/news/news20240105.html",
//         newsDate: "2024/01/05",
//         newsType: "診所公告",
//         newTitle: "休診公告"
//     }, {
//         newsURL: "component/news/news20231115.html",
//         newsDate: "2023/11/15",
//         newsType: "診所公告",
//         newTitle: "診所網站開始運行"
//     },
//     ]

//     let updateList = [{
//         newsURL: "component/news/news20240321.html",
//         newsDate: "2024/55/55",
//         newsType: "診所公告",
//         newTitle: "查詢功能開放"
//     }, {
//         newsURL: "component/news/news20240314.html",
//         newsDate: "2024/55/55",
//         newsType: "診所公告",
//         newTitle: "後台功能新增"
//     }, {
//         newsURL: "component/news/news20240305.html",
//         newsDate: "2024/55/55",
//         newsType: "診所公告",
//         newTitle: "疫苗施打服務"
//     }, {
//         newsURL: "component/news/news20240105.html",
//         newsDate: "2024/55/55",
//         newsType: "診所公告",
//         newTitle: "休診公告"
//     }, {
//         newsURL: "component/news/news20231115.html",
//         newsDate: "2024/55/55",
//         newsType: "診所公告",
//         newTitle: "診所網站開始運行"
//     },]

//     //當點選到第二頁時才更換數據,非第二頁時更換回原數據
//     if (value == 2) {

//         //使用Object.assign直接替換newsList 保留響應式
//         Object.assign(newsList, updateList)
//         console.log("新的newsList", newsList)
//     } else {
//         //使用Object.assign直接替換newsList 保留響應式
//         Object.assign(newsList, oldOneList)
//         console.log("新的newsList", newsList)
//     }


// })


</script>

<style scoped lang="scss">
// section {
    // width: 100%;

    /**最新消息盒子 */
    .newsBox {
        width: 100%;
        margin: 0 auto;

        /**最新消息Title */
        // .newsTitleBox {
        //     text-align: center;
        //     margin: 10% auto;
        //     // font-weight: 700;
        //     font-size: 2.5rem;

        //     /**特殊字樣式 */
        //     .specialFont {
        //         font-family: Satisfy, cursive !important;
        //         font-style: italic;
        //         background: linear-gradient(120deg, #FFF3CD, #FFF3CD);
        //         background-position: 0 80%;
        //         background-repeat: no-repeat;
        //         background-size: 100% 25%;
        //         padding: 0.1875em
        //     }
        // }
        .title-box {
            display: flex;
            justify-content: space-between;
            align-items: center;
            gap: 0.5rem;
            padding-bottom: 1rem;
            position: relative;

            &::after {
                position: absolute;
                content: '';
                display: block;
                width: 100%;
                height: 1px;
                bottom: 0;
                left: 0;
                background-color: #B62D66;
            }


            .title-text-box {
                display: flex;
                .title-image-box {
                    img {
                        width: 2rem;
                    }
                }

                .title {
                    font-size: 2rem;
                    font-weight: bold;
                    color: #B62D66;
                    text-align: start;
                }
            }

            .more-link {
                display: flex;
                text-align: center;
                justify-content: center;
                align-items: center;

                &:hover {
                cursor: pointer;
                scale: 1.05;
                transition: all 0.3s ease-in-out;
            }
            }
        }

        /**最新消息內容盒子 */
        .NewsOuterBox {
            max-width: 1100px;
            margin: 0 auto;

            .no-data {
                font-size: 3rem;

                text-align: center;
            }
            
            /**最新消息內容內部盒子 */
            .NewsInnerBox {
                width: 100%;
                padding: 0;
                display: flex;
                flex-direction: column;
                gap: 0.5rem;

                @media screen and (max-width:481px) {
                    // padding-left: 5%;
                }
                
                /**每個消息 */
                .NewsItem {
                    padding: 1% 0;
                    transition: 0.2s;
                    list-style: none;
                    position: relative;
                    width: 100%;

                    &::before {
                        position: absolute;
                        content: '';
                        display: block;
                        width: 8px;
                        height: 100%;
                        left: 0;
                        top: 0;
                        background-color: #F5C0CB;
                    }

                    &:hover {
                        cursor: pointer;
                        transform: scale(1.02);
                        transition: 0.2s;
                        background-color: #eae5e5;
                    }


                    >a {
                        display: flex;
                        flex-direction: column;
                        justify-content: flex-start;
                        align-items: flex-start;
                        padding-left: 1rem;
                    }
                    
                    /**消息的日期 */
                    .NewsItemDate {
                        color: #cc8761
                    }
                    
                    /**消息的類型 */
                    .NewsItemType {
                    }
                    
                    /**消息的標題 */
                    .NewsItemTitle {
                        font-size: 1.3rem;
                        color: #371307;
                        // width: 100%;
                        overflow: hidden;
                        text-overflow: ellipsis;
                        // white-space: nowrap;

                        @media screen and (max-width:481px) {
                            // width: 96px;

                        }

                    }



                }
            }

            /**分頁組件引入盒子 */
            .example-pagination-block {

                /**重置分頁組件CSS,將分頁組件置中 */
                .el-pagination {
                    justify-content: center;
                }

                &+& {
                    margin-top: 10px;
                }

                .example-demonstration {
                    margin-bottom: 16px;
                }
            }


        }

    }
// }
</style>
