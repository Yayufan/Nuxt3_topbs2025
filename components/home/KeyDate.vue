<template>
    <div class="key-date-section">
        <div class="title-box">
            <div class="title-text-box">
                <div class="title-image-box">
                    <img class="home-banner-bak" src="../../assets/img/CalendarHeatMap.svg">
                </div>
                <h1 class="title">Key Date</h1>
            </div>
        </div>

        <ul class="key-date-item-box">
            <li class="key-date-item">
                <div class="key-date-info">
                    <p class="date-box"><span>15</span><span class="month">May<span class="year">2025</span></span>
                    </p>
                    <p class="info">Abstract Submission Opens</p>
                </div>
                <a class="key-date-link" href="https://evt.to/eiiouhhhw" target="_blank">
                    <img class="home-banner-bak" src="../../assets/img/save date-01.svg">
                </a>
            </li>

            <li class="key-date-item">
                <div class="key-date-info">
                    <p class="date-box"><span>05</span><span class="month">Sep<span class="year">2025</span></span></p>
                    <p class="info">Abstract Submission Deadline</p>
                </div>
                <a class="key-date-link" href="https://evt.to/eiiouhhdw" target="_blank">
                    <img class="home-banner-bak" src="../../assets/img/save date-01.svg">
                </a>
            </li>

            <li class="key-date-item">
                <div class="key-date-info">
                    <p class="date-box"><span>25</span><span class="month">Sep<span class="year">2025</span></span></p>
                    <p class="info">Notification of Acceptance</p>
                </div>
                <a class="key-date-link" href="https://evt.to/eiiouhsmw" target="_blank">
                    <img class="home-banner-bak" src="../../assets/img/save date-01.svg">
                </a>
            </li>

            <li class="key-date-item">
                <div class="key-date-info">
                    <p class="date-box"><span>30</span><span class="month">Sep<span class="year">2025</span></span></p>
                    <p class="info">Early Bird Registration Deadline</p>
                </div>
                <a class="key-date-link" href="https://evt.to/eiiouhsaw" target="_blank">
                    <img class="home-banner-bak" src="../../assets/img/save date-01.svg">
                </a>
            </li>

            <li class="key-date-item">
                <div class="key-date-info">
                    <p class="date-box"><span>15~16</span><span class="month">Nov<span class="year">2025</span></span></p>
                    <p class="info">9th IOPBS & TOPBS2025</p>
                </div>
                <a class="key-date-link" href="https://evt.to/eiiiuaoow" target="_blank">
                    <img class="home-banner-bak" src="../../assets/img/save date-01.svg">
                </a>
            </li>
        </ul>
    </div>
</template>
<script lang="ts" setup></script>
<style lang="scss" scoped>
.key-date-section {
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
                justify-content: flex-start;
                align-items: center;
                text-align: center;

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

    }

    .key-date-item-box {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        gap: 0.5rem;
        padding: 0;

        .key-date-item {
            display: flex;
            gap: 0.5rem;
            width: 100%;

            .key-date-info {
                border-radius: 5px;
                background-color: #F5C0CB;
                padding: 0.3rem 1rem;
                display: flex;
                justify-content: flex-start;
                align-items: center;
                gap: 0.3rem;
                flex: 2;
                width: 90%;
                // min-width: 90%;

                .date-box {
                    color: white;
                    display: flex;
                    flex-direction: column;
                    font-size: 1.3rem;
                    font-weight: bold;
                    position: relative;
                    padding: 0 0.3rem;

                    .month {
                        display: flex;
                        justify-content: center;
                        align-items: center;
                        text-align: center;
                        flex-wrap: none;

                        .year {
                            font-size: 0.6rem;
                            font-weight: normal;
                        }
                    }

                    &::after {
                        position: absolute;
                        content: '';
                        display: block;
                        width: 1px;
                        height: 90%;
                        bottom: 0;
                        right: 0;
                        background-color: white;
                    }
                }

                .info {
                    color: #991D4F;
                    font-size: 1.3rem;
                    font-weight: bold;
                    min-width: 23rem;
                    padding: 0 1rem 0 0;
                    text-wrap: wrap;

                    @media screen and (max-width: 1024px) {
                        font-size: 1rem;
                        min-width: 13rem;

                    }

                    @media screen and (max-width: 768px) {
                        font-size: 1rem;
                        min-width: 80%;
                    }
                }
            }

            .key-date-link {
                background-color: #F5C0CB;
                color: white;
                display: flex;
                justify-content: center;
                align-items: center;
                padding: 0.3rem 0.1rem;
                border-radius: 5px;

                &:hover {
                cursor: pointer;
                scale: 1.05;
                transition: all 0.3s ease-in-out;
            }

                img {
                    width: 2rem;
                }
            }
        }
    }
}
</style>