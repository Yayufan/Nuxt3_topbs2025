<template>
    <main class="common-section">
        <el-carousel class="carousel-section" arrow="always" trigger="click">
            <img class="home-banner-bak" src="@/assets/img/home_banner@2x.png" alt="">
            <el-carousel-item>
                <img src="@/assets/img/home_photo1@2x.png" alt="">
            </el-carousel-item>
            <el-carousel-item>
                <img src="@/assets/img/home_photo2@2x.png" alt="">
            </el-carousel-item>
            <el-carousel-item>
                <img src="@/assets/img/home_photo3@2x.png" alt="">
            </el-carousel-item>
            <el-carousel-item>
                <img src="@/assets/img/home_photo4@2x.png" alt="">
            </el-carousel-item>
        </el-carousel>

        <div class="countdown-timer-section">
            <!-- {{ countdown }} -->
            <div class="countdown-timer" v-html="countdown"></div>
        </div>
        <div class="video-banner">
            <img src="@/assets/img/video_banner.png" alt="">
        </div>
        <div class="video">
            <video src="@/assets/movie/promotionalVideo.mp4" controls></video>
        </div>
    </main>
</template>
<script lang="ts" setup>

const countdown = ref('');

const calculateCountdown = () => {
    const targetDate = new Date('2025/11/15');
    const currentDate = new Date();
    const timeDifference = targetDate.getTime() - currentDate.getTime();

    if (timeDifference > 0) {
        const days = Math.floor(timeDifference / (1000 * 60 * 60 * 24));
        const hours = Math.floor((timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const minutes = Math.floor((timeDifference % (1000 * 60 * 60)) / (1000 * 60));
        const seconds = Math.floor((timeDifference % (1000 * 60)) / 1000);

        countdown.value = `<div> ${days} <span class="countdown-word">Days</span></div>
                            <div>${hours}  <span class="countdown-word">Hours</span> </div>
                            <div>${minutes}  <span class="countdown-word">Minutes</span></div>
                            <div> ${seconds}  <span class="countdown-word">Seconds</span></div>`;
    } else {
        countdown.value = 'Countdown expired';
    }
};

onMounted(() => {
    calculateCountdown();
    setInterval(calculateCountdown, 1000);
});

</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;

    .el-carousel {
        height: 27vw;
        max-width: 100%;
        width: 100;
        margin: 1vw auto 0 auto;

        @media screen and (max-width: 850px) {
            margin: 13vw auto 0 auto;

        }

        .home-banner-bak {
            z-index: 10;
            position: absolute;
            top: 0;
            width: 100%;

            img {
                width: 100%;
                height: 100%;
                object-fit: cover;
                object-position: top center;

            }
        }



        .el-carousel__item {
            width: 100%;
        }

        img {
            width: 100%;
            height: 100%;
            object-fit: content;
            //     object-position: top center;

        }

        :deep(.el-carousel__container) {
            height: 100%;
            width: 100%;
        }

        :deep(.el-carousel__arrow) {
            z-index: 20;
            height: 100%;
            border-radius: 0;
            padding: 0;
            margin: 0;
            opacity: 0.3;
            font-size: inherit;
            text-rendering: auto;

            i {
                width: 2rem;
                height: 2rem;

                svg {
                    width: 3rem;
                    height: 3rem;
                }
            }

            &:hover {
                opacity: 1;
            }
        }

        :deep(.el-carousel__arrow--left) {
            left: 0;
        }

        :deep(.el-carousel__arrow--right) {
            right: 0;
        }

        :deep(.el-icon),
        :deep(.el-icon svg) {
            width: 2rem;
            height: 2rem;
        }

        :deep(.el-carousel__button) {
            width: 0.5rem;
            height: 0.5rem;
            border-radius: 50%;
            color: white;
            opacity: 1;
            z-index: 30;

            &:hover {
                transform: scale(1.65);
                transition: .65s;
            }
        }

        :deep(.el-carousel__indicators) {
            z-index: 30;

            .is-active {
                .el-carousel__button {
                    transform: scale(0.65);
                    transition: .65s;
                }
            }
        }
    }

    .countdown-timer-section {
        // width: $common-section-width;

        height: 10vw;
        width: 100%;
        margin: 0 auto 0 auto;

        // background-color: rgba($color: #000000, $alpha: 0.9);
        background-image: url('/img/bg01.webp');

        color: black;
        font-size: 3.5rem;
        font-weight: bold;
        letter-spacing: 0.1rem;
        text-align: center;
        line-height: 10vw;
        box-sizing: border-box;

        .countdown-timer {
            display: flex;
            justify-content: center;
            margin: 0 auto;
            align-items: center;
            box-sizing: border-box;
            div {
                width: calc(100%/4);
            }
        }

        :deep(.countdown-word) {
            font-size: 2.5rem;
            font-weight: normal;
            letter-spacing: 0rem;
            margin: 0 2.5rem 0 0;
        }

        @media screen and (max-width: 900px) {
            // font-size: 1.5rem;
            // line-height: 6vw;
            justify-content: space-around;
            div {
                // width: calc(100%/4);
                // margin: auto;
            }

            :deep(.countdown-word) {
                font-size: 1rem;
                margin: 0 0.5rem 0 0;
            }

        }
    }

    .video-banner {
        width: $common-section-width;
        margin: 5vw auto 0 auto;

        img {
            width: 100%;
        }
    }

    .video {
        width: $common-section-width;
        margin: $common-section-margin;

        video {
            width: 100%;
        }
    }
}
</style>