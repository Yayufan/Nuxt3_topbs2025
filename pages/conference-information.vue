<template>
    <div>
        <main class="common-section">
            <Breadcrumbs firstRoute="IOPBS & TOPBS" secoundRoute="Conference Information"></Breadcrumbs>
            <Title title="Conference Information"></Title>

            <div class="content">
                <div class="table-box">
                    <table class="table">
                        <tr>
                            <th>Over View</th>
                            <th>Content</th>
                        </tr>
                        <tr>
                            <td class="over-view">Conference Title</td>
                            <td><p>International Oncoplastic Breast Surgery Symposium &</p> 
                                <p>Taiwan Oncoplastic Breast Surgery Society</p>
                            </td>
                        </tr>
                        <tr>
                            <td class="over-view">Date</td>
                            <td>November 15-16, 2025</td>
                        </tr>
                        <tr>
                            <td class="over-view">Venue</td>
                            <td>
                                <p>Taipei International Convertion Center</p>
                                <p>No.1 Hsin-Yi Road, Section 5,Taipei 11049,Taiwan</p>
                            </td>
                        </tr>
                        <tr>
                            <td class="over-view">Official Language</td>
                            <td>English</td>
                        </tr>
                        <tr>
                            <td class="over-view">Organized by</td>
                            <td>9th IOPBS &TOPBS 2025</td>
                        </tr>
                    </table>
                </div>

                <div class="img-box">
                    <img class="pc-time-line" src="../assets/img/timeline--w1920px.png" alt="timeline">
                    <img class="mobile-time-line" src="../assets/img/timeline--w800px.png" alt="timeline">
                </div>
            </div>
        </main>
    </div>
</template>
<script setup lang="ts">
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Title from '@/components/layout/Title.vue';

useSeoMeta({
    title: 'Conference Information - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Explore the conference information for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. This page is currently under construction, but stay tuned for updates on the event details, schedule, and more.',
    keywords: 'Conference Information, 9th IOPBS, IOPBS 2025, TOPBS 2025, 2025 IOPBS, 2025 TOPBS '
})

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

        .table-box {
            width: 100%;
            margin: 0 auto;
            overflow-x: auto;

            .table {
                width: 70%;
                margin-inline: auto;
                border-collapse: collapse;
                text-align: center;

                th,
                td {
                    border: 1px solid #ddd;
                    padding: 2rem;
                    text-align: left;
                    font-weight: bold;
                    font-size: 1.5rem;
                }

                th {
                    background-color: #E8979E;
                    text-align: center;
                    color: white;
                }

                .over-view {
                    text-align: center;
                    background-color: #F2F2F2;
                    font-weight: bold;
                }
            }
        }

        .img-box {
            width: 70%;
            margin: 2rem auto;
            display: flex;
            justify-content: center;
            img {
                width: 70%;
                height: auto;
            }

            .pc-time-line {
                display: block;
            }
            .mobile-time-line {
                display: none;
            }

            @media screen and (max-width: 800px) {
                .pc-time-line {
                    display: none;
                }
                .mobile-time-line {
                    display: block;
                }
            }
        }

    }
}
</style>