<template>
    <div>
        <main class="common-section">
            <div class="banner-box">
                <img src="../assets//img/banner.png" alt="">
            </div>
            <div class="title-section">
                <p class="title">
                    Transportation
                </p>
            </div>
            <div class="map-box">
                <iframe class="google-map"
                    src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3615.0165568738184!2d121.55831637622504!3d25.033512177816732!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3442abb61ab3d33f%3A0xab0d0f7ac395bff4!2z5Y-w5YyX5ZyL6Zqb5pyD6K2w5Lit5b-DKFRJQ0Mp!5e0!3m2!1szh-TW!2stw!4v1739263463546!5m2!1szh-TW!2stw"
                    height="450" style="border:0;" allowfullscreen="false" loading="lazy"
                    referrerpolicy="no-referrer-when-downgrade"></iframe>
            </div>
            <div class="map-info">
                <p class="map-info-item">Taipei International Convertion Center</p>
                <p class="map-info-item">No.1 Hsin-Yi Road, Section 5,Taipei 11049,Taiwan</p>
                <p class="map-info-item">Tel. +886(2)2725-5200/+886(2)2723-2589</p>
                <p class="map-info-item">Email: ticc@taitra.org.tw</p>
            </div>
            <div class="shadow-divider"></div>
            <div class="transportation-1">
                <img src="../assets/img/transport.png" alt="">
            </div>

            <div class="transport-table">
                <table>
                    <tr>
                        <th class="left-top-corner"> </th>
                        <th>Line/Timetable</th>
                        <th>Travel Time</th>
                        <th class="right-top-corner">Fare</th>
                    </tr>
                    <tr class="row-2">
                        <td>
                            <p class="transportation">Taoyuan Airport MRT</p>
                        </td>
                        <td>
                            <div>Terminal 1: <span>A12</span> <el-icon>
                                    <ElIconRight />
                                </el-icon> <span>A1</span></div>
                            <div>Terminal 2: <span>A13</span> <el-icon>
                                    <ElIconRight />
                                </el-icon> <span>A1</span></div>
                        </td>
                        <td>50 mins</td>
                        <td>NTD $160</td>
                    </tr>
                    <tr class="row-3">
                        <td>
                            <p class="transportation">Taipei Songshan Airport MRT</p>
                        </td>
                        <td>
                            <p>Songshan Airport: <span>BR13</span> <el-icon>
                                    <ElIconRight />
                                </el-icon> <span>R03</span></p>
                        </td>
                        <td>17 mins</td>
                        <td>NTD $25</td>
                    </tr>
                    <tr class="row-4">
                        <td>
                            <p class="transportation">MRT</p>
                        </td>
                        <td>
                            <p>Taipei Main Station</p>
                            <div><span>BL12</span><span>R10</span><el-icon>
                                    <ElIconRight />
                                </el-icon><span>BR09</span><span>R05</span><el-icon>
                                    <ElIconRight />
                                </el-icon><span>R03</span>
                            </div>
                        </td>
                        <td>15 mins</td>
                        <td>NTD $25</td>
                    </tr>
                    <tr class="row-5">
                        <td>
                            <p class="transportation">iBus(1960)</p>
                            <span class="small-font transportation-hint">Bus location</span>
                            <div class="small-font transportation-hint">
                            <div>Terminal 1:</div>
                            <div>
                                <div>Passenger bus</div>
                                <div>waiting area on Floor B1</div>
                            </div>
                            </div>
                            <div class="small-font transportation-hint">
                            <div>Terminal 2:</div>
                            <div>
                                <div>Passenger bus</div>
                                <div>waiting area on the 1st
                                    floor</div>
                            </div>
                            </div>
                        </td>
                        <td>
                            Terminal 1/2 -> Grand Hyatt Taipei
                            <div class="bus-timetable">
                                <span class="small-font">TimeTable:</span>
                                <span class="small-font">00:15、12:40、06:50、07:30、09:00、10:20、
                                </span>
                                <span class="small-font">11:20、12:40、
                                    14:00、15:00、15:40、17:40、</span>
                                <span class="small-font">19:10、21:10、22:40</span>
                            </div>
                        </td>
                        <td>90 mins</td>
                        <td>NTD $190</td>

                    </tr>
                    <tr>
                        <td class="left-bottom-corner" :rowspan="2">
                            <div class="transportation">Taxi</div>
                        </td>
                        <td>Taiyuan Airport -> TICC</td>
                        <td>1-1.5 hr</td>
                        <td>NTD $1310</td>

                    </tr>
                    <tr>
                        <td>Taipei Songshan Airport MRT -> TICC</td>
                        <td>10-30 mins</td>
                        <td class="right-bottom-corner">NTD $225</td>
                    </tr>
                </table>
            </div>

            <div class="paragraph">Taoyuan Airport MRT</div>
            <div class="mrt-img-box">
                <img src="../assets/img/mrt_en.jpg" alt="">
            </div>
            <div class="paragraph">MRT(Taiwan High Speed Rall)</div>
            <div class="taipei-mrt-img-box">
                <img src="../assets/img/metrotaipeimap.jpg" alt="">
            </div>

            <div class="back-to-top" @click="backToTop">
            <img src="../assets/img/top.png" alt="">
        </div>
        </main>

      

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'

const backToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: 'smooth'
  });
}
</script>
<style lang="scss" scoped>
.common-section {
    // width: $common-section-width;
    // margin: $common-section-margin;
    font-family: $common-section-font-family;

    .content {
        margin: 1rem auto;
        text-align: center;

        h1 {
            font-size: 2rem;
        }
    }

    .banner-box {
        margin-top: 1rem;

        img {
            width: 100%;
            box-shadow: 0px 6px 10px 0px rgba(0, 0, 0, 0.5);
        }
    }

    .title-section {
        margin-top: 1rem;
        text-align: center;
        position: relative;

        .title {
            font-size: 2.7rem;
            font-weight: 600;
        }

    }

    .map-box {
        width: 100%;
        display: flex;
        justify-content: center;

        .google-map {
            width: 70%;
            height: 60vh;
        }
    }

    .map-info {
        width: 70vw;
        display: flex;
        justify-content: flex-start;
        flex-direction: column;
        align-items: flex-start;
        margin: 1rem auto;

        .map-info-item {
            font-size: 1.5rem;
            letter-spacing: 0.1rem;
            margin: 0.5rem 0;
        }
    }

    .transportation-1 {
        display: flex;
        justify-content: flex-start;
        flex-direction: column;
        align-items: flex-start;

        img {
            margin: 3% auto;
            width: 88%;
        }
    }

    .mrt-img-box {
        display: flex;
        margin: 1rem auto;
        width: 80%;

        img {
            width: 100%;
        }
    }

    .taipei-mrt-img-box {
        display: flex;
        margin: 1rem auto;
        width: 80%;

        img {
            width: 100%;
        }
    }

    .paragraph {
        font-size: 2rem;
        color: #D36672;
        margin: 1rem auto;
        padding-left: 10rem;
        position: relative;

        &::before {
            content: '';
            position: absolute;
            width: 8rem;
            height: 5px;
            background-color: #D36672;
            left: 0;
            top: 1.1rem;
        }
    }

    .shadow-divider {
        width: 85%;
        height: 2px;
        margin: 1rem auto;
        background-image: repeating-linear-gradient(to right,
                #CDCBCB,
                #CDCBCB 30px,
                transparent 5px,
                transparent 50px);
    }

    .back-to-top {
        position: fixed;
        bottom: 27%;
        right: 2rem;
        width: 4rem;
        height: 4rem;

        img {
            width: 100%;
        }
    }

    .transport-table {
        width: 85%;
        margin: 1rem auto;
        font-family: "思源黑體", "Arial", sans-serif;
        p {
            display: inline-block !important;
        }


        table {
            width: 100%;
            border-collapse: separate;
            border-spacing: 0;
            border: 1px solid black;
            border-radius: 15px;
            text-align: start;

            th {
                padding: 1rem;
                font-size: 1.3rem;
                background-color: #D36672;
                border: 1px solid black;

                color: white;
                text-align: center;
            }

            td {
                padding: 1rem 0.1rem 1rem 1rem;
                // text-wrap: nowrap;
                font-size: 1.3rem;
                border: 1px solid black;

            }

            .transportation {
                padding: 0.2rem 2rem;
                font-size: 1.5rem;
                text-wrap: nowrap;
                color: #D36672;
            }

            .row-2 {
                padding: 0 1rem;

                td {

                    div {
                        margin: 0.5rem 0 0.5rem 0;
                        display: flex;
                        align-items: center;
                    }

                    span {
                        background-color: #70448E;
                        color: white;
                        border-radius: 13px;
                        font-weight: normal;
                        padding: 0.5rem 1rem;
                        margin: 0 0.5rem;
                    }
                }
            }

            .row-3 {
                text-align: start;
                padding: 0 1rem;

                td {
                    text-align: start;

                    p {
                        margin: 0.5rem 0 0 0;
                        display: flex;
                        align-items: center;
                    }

                    span {
                        &:first-child {
                            background-color: #B78537;
                        }

                        &:last-child {
                            background-color: #C7182D;
                        }

                        color: white;
                        font-weight: normal;
                        border-radius: 13px;
                        padding: 0.5rem 1rem;
                        margin: 0 0.5rem 0 0.5rem;
                    }
                }
            }

            .row-4 {
                text-align: start;
                padding: 0 1rem;

                td {
                    text-align: start;

                    div {
                        margin: 0.5rem 0 0 0;
                        display: flex;
                        align-items: center;
                        text-wrap: nowrap;
                    }

                    span {

                        &:nth-child(even),
                        &:last-child {
                            background-color: #C7182D;
                        }

                        &:nth-child(1) {
                            background-color: #1165A6;
                        }

                        &:nth-child(5) {
                            background-color: #B78537;
                        }

                        color: white;
                        font-weight: normal;
                        border-radius: 13px;
                        padding: 0.5rem 1rem;
                    }
                }
            }

            .row-5 {
                td {

                    p {
                        margin: 0.5rem 0 0 0;
                        display: flex;
                        align-items: center;
                    }

                    .small-font {
                        font-size: 1rem;
                        font-weight: normal;
                    }

                    .transportation-hint {
                        font-size: 1rem;
                        padding: 0 2rem;
                        text-wrap: nowrap;
                        display: flex;
                        align-items: flex-start;
                    }

                    .bus-timetable {
                        width: 65%;
                        background-color: #D36672;
                        border-radius: 10px;
                        color: white;
                        padding: 0.5rem 0.5rem;
                        text-align: start;
                        display: flex;
                        flex-direction: column;
                        margin-top: 0.5rem;

                        span {
                            margin: 0rem 0 0 1rem;
                        }
                    }
                }
            }

            .left-top-corner {
                border-top-left-radius: 15px;
            }

            .left-bottom-corner {
                border-bottom-left-radius: 15px;
            }

            .right-top-corner {
                border-top-right-radius: 15px;
            }

            .right-bottom-corner {
                border-bottom-right-radius: 15px;
            }
        }
    }

   

}
</style>