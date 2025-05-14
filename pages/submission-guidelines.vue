<template>
    <div>
        <main class="common-section">
            <Banner></Banner>
            <Breadcrumbs firstRoute="Abstracts" secoundRoute="Submission Guidelines"></Breadcrumbs>
            <Title title="Submission Guidelines"></Title>

            <div class="content">
                <!-- <h1 class="sub-title">Submission Guidelines</h1> -->
                <h1 class="">Important Dates</h1>

                <div class="important-date-info">
                    <ul class="disc-list">
                        <li class="note-text">Abstract Submission Deadline: Friday, September 5, 2025 </li>
                        <li>Abstract Results Announcement: Thursday, September 25, 2025 </li>
                        <li>E-Poster & Video Submission Deadline: Friday, October 10, 2025 </li>
                    </ul>
                </div>

                <div class="review-process">
                    <h1>Review Process</h1>
                    <table class="review-process-table">
                        <tr>
                            <td rowspan="2">Step1</td>
                            <td>May15 ~ September 5</td>
                            <td>Submit abstracts online after complete registration on the official website </td>
                        </tr>

                        <tr>
                            <td>September 6 ~ September 24 </td>
                            <td>Abstracts will be reviewed by the committee </td>
                        </tr>

                        <tr>
                            <td rowspan="4">
                                Step2
                            </td>
                            <td>September 25 </td>
                            <td>Notification of accepted abstracts </td>
                        </tr>

                        <tr>
                            <td>September 25 ~ October 10 </td>
                            <td>E-poster & video upload to the official website. </td>
                        </tr>

                        <tr>
                            <td>October 10 ~ 23 </td>
                            <td>Committee reviews accepted e-posters and videos to select award winners </td>
                        </tr>
                        <tr>
                            <td>October 24 </td>
                            <td>Award announcement </td>
                        </tr>
                        <tr>
                            <td>Oral Presentation & Award Ceremony </td>
                            <td>November 15 </td>
                            <td>The winners will give oral presentations and receive awards </td>
                        </tr>
                        <tr>
                            <td>Exhibition of Selected Abstract </td>
                            <td>November 15 ~ 16 </td>
                            <td>All selected e-posters and videos will be displayed at the event venue. </td>
                        </tr>
                    </table>
                </div>


                <div class="abstract-submission-box">
                    <h1 class="submission-title">[Abstract Submission]</h1>

                    <div class="submission-guidelines-box">
                        <h2>01. How to confirm your abstract presentation </h2>
                        <ul class="secondstep-list">
                            <li><B>Step 1:</B> Register and <nuxt-link class="link" to="/login"> sign in</nuxt-link>.
                            </li>

                            <li><B>Step 2:</B> Complete online registration before submitting your
                                abstract.
                            </li>
                            <li><B>Step 3:</B> Click “Abstract” → “Submit Online” on the website, fill in all required
                                information, and upload your abstract. </li>
                            <li><B>Step 4:</B> Check your email for confirmation of successful submission. </li>
                        </ul>
                    </div>

                    <div class="submission-guidelines-box">
                        <h2>02. Abstract Format </h2>
                        <p class="list-text">Only PDF files submitted through the official website will be accepted.
                            Submissions via email, post, or fax are not accepted. </p>

                        <ul class="disc-list">
                            <li>Title: Tahoma font, 14pt; capitalize only the first word, proper nouns, and
                                abbreviations;
                                avoid abbreviations in the title. </li>
                            <li>Body: Include purpose, methods, results, and conclusion; Tahoma font, 11pt; line spacing
                                18pt; margin 1.5 cm; no figures, tables, references, or keywords allowed. </li>
                            <li>Authors: Up to 30 authors. Institutions should list hospitals first, followed by
                                universities. </li>
                            <li>If the author is affiliated with both, list the hospital name. </li>
                        </ul>
                    </div>

                    <div class="submission-guidelines-box">
                        <h2>03. Submission Notes </h2>
                        <ul class="disc-list">
                            <li>The presenting author must be the first author. Only one presenter per abstract. </li>
                            <li>All fields in the online submission form must be completed. </li>
                            <li>The abstract title should reflect the research topic and must not contain results or
                                conclusions. </li>
                            <li>Commercial names may be used in the abstract body but must include the ® symbol. </li>
                            <li>Abbreviations in the abstract body must be defined. </li>
                            <li>Authors Must indicate which award category they wish to apply for; final selection is at
                                the
                                discretion of the 9th IOPBS & TOPBS 2025 Committee. </li>
                        </ul>
                    </div>

                    <div class="submission-guidelines-box">
                        <h2>04. Conflict of Interest Disclosure </h2>
                        <ul class="disc-list">
                            <li>All authors must disclose any potential conflicts of interest when submitting the
                                abstract.
                            </li>
                            <li>The presenting author is responsible for collecting and submitting this information for
                                all
                                co-authors. </li>
                        </ul>
                    </div>

                    <div class="submission-guidelines-box">
                        <h2>05. Acceptance Notification </h2>
                        <ul class="disc-list">
                            <li>Notifications will be sent via email.</li>
                            <li>All abstracts will be reviewed according to standard procedures. </li>
                            <li>The committee reserves the right to make final decisions on abstract acceptance. </li>
                        </ul>
                    </div>


                    <div class="submission-guidelines-box">
                        <h2>06. Abstract Modification or Withdrawal </h2>
                        <ul class="disc-list">
                            <li>Abstracts will be withdrawn if registration is incomplete. </li>
                            <li>Submitted abstracts may be modified online before the Submission deadline. </li>
                            <li>To modify an accepted abstract, contact the 9th IOPBS & TOPBS 2025 Secretariat by email
                                within 36 hours of receiving the acceptance notification. </li>
                        </ul>
                    </div>

                    <div class="submission-guidelines-box">
                        <h2>07. Other Submission Policies </h2>
                        <ul class="disc-list">
                            <li>Abstracts submitted must not have been previously published in peer-reviewed journals or
                                presented at other conferences. </li>
                            <li>Submission of encore abstract is not allowed; for follow-up studies, new data must be
                                included. </li>
                            <li>Abstracts that violate guidelines or are submitted after the deadline will be rejected.
                            </li>
                            <li>Submission implies that the first and co-authors agree to grant usage rights, ensure
                                data
                                accuracy, and take responsibility for communication. </li>

                        </ul>
                    </div>
                </div>

                <p class="reminder note-text">The 9th IOPBS & TOPBS 2025 reserves the right to modify event rules and
                    program
                    content. In case of dispute, the committee’s decision is final. </p>

                <el-divider></el-divider>

              

                <!-- <el-button>
                    Online Submission
                </el-button> -->


            </div>
        </main>

    </div>
</template>
<script setup lang="ts">
import Banner from '@/components/layout/Banner.vue';
import Title from '@/components/layout/Title.vue';
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
</script>
<style lang="scss" scoped>
.common-section {
    margin: $common-section-margin;
    font-family: $common-section-font-family;

    .content {
        width: 60%;
        margin-inline: auto;
        font-size: 1.5rem;
        line-height: 2.5rem;

        .title {
            padding: 2rem 4rem 2rem 0;
            font-size: 2.5rem;
        }

        .important-date-info {
            border: $accent-color 1px solid;
            padding: 2rem;

            ul {
                display: flex;
                flex-direction: column;
                gap: 1rem;
                font-size: 1.5rem;
            }
        }

        .reminder {
            margin: 1rem 0;
            font-size: 1rem;
            line-height: normal;
        }

        .submission-title {
            margin-top: 4rem;
            text-align: center;
        }

        .step-box-list {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 1rem 2rem 2rem;
            border-radius: 1rem;
            gap: 2rem;
            width: 100%;

            .step-box {
                display: flex;
                border: 1px solid #DE6A75;
                border-radius: 10px;
                padding: 1rem;
                min-width: 30%;
                justify-content: center;

                .step {
                    display: flex;
                    align-items: center;
                    gap: 1rem;

                    h3 {
                        background-color: #DE6A75;
                        padding: 0.3rem 0.5rem;
                        border-radius: 5px;
                        font-weight: normal;
                        color: white;
                    }

                    p {
                        position: relative;

                    }
                }
            }
        }

        h2 {
            font-size: 2rem;
        }

        .step-list {
            list-style-type: decimal;

            .step-list-item {
                white-space: pre-wrap;
            }
        }

        .disc-list {
            list-style-type: disc;
        }

        .no-type-list {
            list-style: none;
        }

        .decimal-list {
            list-style-type: decimal;
        }

        .square-list {
            list-style: square;
        }

        .shadow-divider {
            // width: 85%;
            height: 2px;
            margin: 1rem auto;
            background-image: repeating-linear-gradient(to right,
                    #CDCBCB,
                    #CDCBCB 30px,
                    transparent 5px,
                    transparent 50px);
        }


        .submission-guidelines-box {
            margin-top: 4rem;
        }

        .list-text {
            padding: 1rem 0 0 1rem;
            font-size: 1.3rem;
            line-height: normal;
        }

        .main-list {
            list-style-type: decimal-leading-zero;
        }



        .third-list {
            padding-left: 4rem;
            font-size: 1.2rem;
        }

        .note-text {
            color: #DE6A75;
        }

        .sub-title {
            margin-top: 4rem;
            font-size: 1.5rem;
            font-weight: bold;
            color: $accent-hover-bg;
        }

        .submission-title {
            font-weight: bold;
            color: $accent-hover-bg;
        }

        .review-process-table {
            width: 100%;
            border-collapse: collapse;
            // margin: 2rem 0;

            td {
                padding: 1rem;
                border: 1px solid black;
                text-align: center;
                font-size: 1.2rem;
                line-height: normal;
            }
        }

        .link {
            color: #2667B9;
            text-decoration: underline;
        }



        @media screen and (max-width: 486px) {
            width: 90%;
        }
    }

}
</style>