<template>
    <div>
        <main class="common-section">
            <Banner></Banner>
            <Breadcrumbs firstRoute="Abstracts" secoundRoute="Award" />
            <Title title="Award"></Title>

            <div class="content">
                <p>The organizing committee of TIBCS 2024 will select outstanding abstracts for a variety of awards. 3
                    winners of Young Investigator Award/ 3 winners of Best Presentation Awards/ 1 winner of Brilliant
                    Presentation Award and 5 winners of Selected Presentation Award will be notified on Oct. 26. The
                    ranking and the awards will be announced in the ceremony on Oct. 27.</p>


                <ul class="main-list">

                    <li>
                        <B>Young Investigator Award</B>
                        <ul class="second-list">
                            <li>Scholars: 1 winners</li>
                            <li>Benefits:</li>
                            <ul class="third-list">
                                <li>The 1st place: USD 800 and certificate</li>
                            </ul>
                            <li>Qualification:</li>
                            <ul class="third-list">
                                <li>Applicants who are 45 years old and under are eligible to win the TIBCS Young
                                    Investigator Award.</li>
                                <li>Applicants who have complete registration and submission their abstract on the
                                    website.
                                    After accepted, the applicants must submit the e-poster and recoding file on the
                                    website. The committee will select top 3 to have oral presentation.</li>
                            </ul>
                        </ul>
                    </li>

                    <li>
                        <B>Best Video Award</B>
                        <ul class="second-list">
                            <li>Scholars: 1 winners</li>
                            <li>Benefits:</li>
                            <ul class="third-list">
                                <li>The 1st place: USD 800 and certificate</li>
                            </ul>
                        </ul>
                    </li>

                    <li>
                        <B>Best Poster Award</B>
                        <p class="list-text">According to the review of all the submitted e-posters and recording files by the committee,
                            the
                            4th place will be the winner of Brilliant Presentation Award, and the 5-9th place will be
                            the
                            winners of Selected Presentation Award.</p>
                        <ul class="second-list">
                            <li>Scholars: 1 winners</li>
                            <li>Benefits:</li>
                            <ul class="third-list">
                                <li>The 1st place: USD 800 and certificate</li>
                            </ul>
                        </ul>
                    </li>
                </ul>

                <div class="award-geremony">
                    <ul class="second-list">
                        <li><B>Date:</B></li>
                        <li><B>Venue:</B></li>
                        <li>Please note that for those who are not present, it would be considered as waiving the
                            awards.</li>
                    </ul>
                </div>

                <p class="reminder">
                    For general enquiries, please contact the Secretariat of  by email
                    (iopbs2025@gmail.com).
                </p>

                <p class="warn">IOPBS reserves the right to amend the program of the rules and regulations. Should
                    there be disputes, IOPBS reserves the right to the final decision.

                </p>

            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue';
import Title from '@/components/layout/Title.vue';
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
            list-style: decimal-leading-zero;
            display: flex;
            flex-direction: column;
            gap: 5rem;
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

        .reminder {
            font-size: 1.2rem;
        }

        .warn {
            font-size: 0.8rem;
            text-align: center;
        }

        @media screen and (max-width: 476px) {
            width: 80%;
        }
    }
}
</style>