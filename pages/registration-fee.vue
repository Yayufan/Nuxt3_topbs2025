<template>
    <div>
        <main class="common-section">
            <Banner />

            <Breadcrumbs firstRoute="Registration" secoundRoute="Registration Fee"></Breadcrumbs>

            <Title :title="'Registration Fee'"></Title>
            <table class="personal-registration-table">
                <tr class="personal-row-1">
                    <th class="category-col" :rowspan="2" :colspan="2">Category</th>
                    <th :colspan="2">Only Physical</th>
                </tr>
                <tr class="personal-row-2">
                    <th>
                        <p>Early-Bird</p>
                        <p>(before Sep 30, 2025)</p>
                    </th>
                    <th>
                        <p>Onsite</p>
                        <p>(Oct 1- Nov 16, 2025)</p>
                    </th>
                </tr>
                <tr class="personal-row-3">
                    <td :rowspan="2">
                        <p class="category-item">Professor/</p>
                        <p class="category-item">Physician/</p>
                        <p class="category-item">Company</p>
                    </td>
                    <td>Non-member</td>
                    <td>USD 400</td>
                    <td>USD 500</td>
                </tr>
                <tr class="personal-row-4">
                    <td>Member</td>
                    <td>USD 300</td>
                    <td>USD 400</td>
                </tr>
                <tr class="personal-row-5">
                    <td :colspan="2">
                        <p class="category-item">Trainee/Nurse/Researcher</p>
                    </td>
                    <td>USD 150</td>
                    <td>USD 200</td>

                </tr>
            </table>
            <p class="tips">*The prices are listed in USD. According to the financial regulations in Taiwan, the actual
                credit card payment will be charged in TWD or your local currency. It may be a little different from the
                price listed above. </p>
            <div class="btn-section"> <nuxt-link class="register-btn" to="/online-registration">Register Now
                    !</nuxt-link>
            </div>
            <div class="shadow-divider"></div>

            <Title :title="'Group Registration'"></Title>

            <table class="group-registration-table">
                <tr class="group-row-1">
                    <th>
                        <p>Minimum Number of Persons</p>
                        <p>Required for Group Registration</p>
                        <p>(Foreigners ONLY: Professor, Physician and Company)</p>
                    </th>
                    <th>
                        <p>Benefit</p>
                    </th>
                    <th>
                        <p>Payment</p>
                        <p>Method</p>
                    </th>
                    <th>
                        <p>Deadline</p>
                    </th>
                </tr>
                <tr>
                    <td>
                        <p>5 persons</p>
                    </td>
                    <td>
                        <p>10% Discount</p>
                    </td>
                    <td>
                        <p>Credit card</p>
                    </td>
                    <td>
                        <p>9/30</p>
                    </td>
                </tr>
            </table>
            <table class="mobile-group-registration-table">
                <tr>
                    <td>
                        <p>Minimum Number of Persons</p>
                        <p>Required for Group Registration</p>
                        <p>(Foreigners ONLY: Professor, Physician and Company)</p>
                    </td>
                    <td>
                        <p>5 persons</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p>Benefit</p>
                    </td>
                    <td>
                        <p>10% Discount</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p>Payment</p>
                        <p>Method</p>
                    </td>
                    <td>
                        <p>Credit card</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p>Deadline</p>
                    </td>
                    <td>
                        <p>9/30</p>
                    </td>
                </tr>
            </table>

            <p class="tips">*Please fill in the form completely</p>
            <p class="tips">*The credit card transaction page will be given through email to the sender.</p>
            <p class="tips">*Payment for group registration must be paid at once by one person.</p>
            <div class="btn-section"> <nuxt-link class="group-register-btn"
                    to="/registration-now/group-registration">Group Registration Form</nuxt-link>

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
        text-align: center;

        h1 {
            font-size: 2rem;
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

    .personal-registration-table {
        width: 90vw;
        margin: 1rem auto;
        font-size: 1.5rem;
        font-weight: 600;
        color: #383A51;

        @media screen and (max-width: 768px) {
            font-size: 1rem;
        }

        @media screen and (max-width: 425px) {
            font-size: 10px;
        }

        th {
            color: white;
            background-color: #DE6A75;
            border: 1px solid #EEE2DC;
            padding: 1rem;
        }

        td {
            background-color: #FEECE8;
            padding: 1rem;
            border: 1px solid #EEE2DC;

            .category-item {
                color: #7A2D67;
            }
        }

        .personal-row-1 {
            .category-col {
                padding: 2rem 0.5rem;
                text-align: start;
                border: #F29EA6 1px solid;
                width: 50%;
            }
        }
    }

    .tips {
        width: 88vw;
        margin: 1rem auto;
        text-align: start;
        font-size: 1rem;
        font-weight: 600;
    }

    .btn-section {
        margin: 2rem auto 4rem auto;
        text-align: center;

        .register-btn {
            min-width: 13rem;
            background-color: #DE6A75;
            color: white;
            padding: 1rem 2rem;
            font-weight: 600;
            letter-spacing: 0.1rem;
            border-radius: 10px;

            &:hover {
                cursor: pointer;
            }
        }

        .group-register-btn {
            min-width: 13rem;
            background: linear-gradient(to right, #E28A90, #A4557D);
            color: white;
            padding: 1.3rem 2rem;
            font-weight: 600;
            letter-spacing: 0.1rem;
            border-radius: 10px;
        }
    }

    .group-registration-table {
        width: 90vw;
        margin: 1rem auto;
        font-size: 1.5rem;
        font-weight: 600;

        @media screen and (max-width: 768px) {
            display: none;
        }

        th {
            padding: 1rem;
            border: 1px solid #EEE2DC;

            &:first-child {
                text-align: start;
            }
        }

        td {
            background-color: #FEECE8;
            padding: 1rem;
            border: 1px solid #EEE2DC;
            color: #7A2D67;

            &:not(:first-child) {
                text-align: center;
            }
        }

        .group-row-1 {
            background: linear-gradient(to right, #E28A90, #A4557D);
            color: white;
        }
    }

    .mobile-group-registration-table {
        display: none;
        width: 90vw;
        margin: 1rem auto;
        font-size: 1.5rem;
        font-weight: 600;

        @media screen and (max-width: 768px) {
            display: block;
        }

        td {
            padding: 1rem;
            border: 1px solid #EEE2DC;
           &:first-child {
                background: linear-gradient(to right, #E28A90, #A4557D);
                color: white;
                width: 60%;
            }

            &:not(:first-child) {
                background-color: #FEECE8;
                color: #7A2D67;
                text-align: center;
            }
        }
    }
}
</style>