<template>
    <div>
        <main class="common-section">
            <Banner></Banner>
            <Breadcrumbs firstRoute="Abstracts" secoundRoute="Award" />
            <Title title="Award"></Title>

            <div class="content">
                <p>The 9th IOPBS & TOPBS 2025 Organizing Committee will select outstanding submissions from the
                    abstracts received and present the following awards: Young Investigator Award (1 winner), Best
                    Poster Award (1 winner), and Best Video Award (1 winner).
                    The award results will be announced on Friday, October 24, and the winners will give an oral
                    presentation and receive their awards on Saturday, November 15. </p>


                <ul class="main-list">

                    <li>
                        <B>01.Young Investigator Award</B>
                        <ul class="second-list">
                            <li>Number of Winners: 1 </li>
                            <li>Award: USD 800 and a Young Investigator Award certificate </li>
                            <li>Eligibility:
                                <ul style="list-style-type: circle;">
                                    <li>Researchers aged 45 or younger. </li>
                                    <li>Must complete online registration and submit an abstract. Upon acceptance, an
                                        e-poster must be submitted.

                                    </li>
                                </ul>

                            </li>
                        </ul>
                    </li>

                    <li>
                        <B>02.Best Poster Award</B>
                        <ul class="second-list">
                            <li>Number of Winners: 1 </li>
                            <li>Award: USD 800 and a Best Poster Award certificate </li>
                            <li>Eligibility:
                                <ul style="list-style-type: circle;">
                                    <li>Must complete online registration and submit an abstract. Upon acceptance, an
                                        e-poster must be submitted.
                                    </li>
                                </ul>

                            </li>
                        </ul>
                    </li>

                    <li>
                        <B>03.Best Video Award </B>
                        <ul class="second-list">
                            <li>Number of Winners: 1 </li>
                            <li>Award: USD 800 and a Best Video Award certificate </li>
                            <li>Eligibility:
                                <ul style="list-style-type: circle;">
                                    <li>Must complete online registration and submit an abstract. Upon acceptance, a video file must be submitted. 
                                    </li>
                                </ul>

                            </li>
                        </ul>
                    </li>
                </ul>

             
                <ul class="none-style-list">
                    <li><B>Note:</B>
                        <ul class="disc-list">
                            <li>All prize amounts are before tax.</li>
                            <li>The organizer reserves the right to withhold awards if there is an insufficient number of submissions or due to other related reasons. </li>
                        </ul>
                    </li>
                </ul>
            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue';
import Title from '@/components/layout/Title.vue';

useSeoMeta({
    title: 'Award - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Discover the award opportunities at the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. The organizing committee will present awards for Young Investigator, Best Poster, and Best Video. Winners will be announced on October 24 and recognized during the conference.',
    keywords: 'Abstract Award, Award, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;

    .content {
        margin: 1rem auto;
        width: 60%;
        font-size: 1.5rem;
        line-height: 2.5rem;

        .main-list {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 5rem;
            padding: 0;
        }

        .second-list {
            list-style: disc;
            font-size: 1.3rem;

        }

        .third-list {
            list-style: square;
            font-size: 1.2rem;
        }

        .list-text {
            font-size: 1.3rem;
            margin: 1rem 0;
        }

        .none-style-list {
            list-style: none;
            margin: 1rem 0;
            font-size: 1.3rem;
                        padding: 0;

        }

        .disc-list {
            list-style: disc;
            margin-left: 2rem;
            font-size: 1.3rem;
        }



        @media screen and (max-width: 476px) {
            width: 80%;
        }
    }
}
</style>