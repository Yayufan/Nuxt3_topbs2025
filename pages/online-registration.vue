<template>
    <main class="common-section">
        <Banner />
        <Breadcrumbs :first-route="'Registration'" :secound-route="'Online Registration'" />
        <div class="title-section">
            <p class="title">
                Online Registration
            </p>
        </div>

        <div class="select-section">
            <!-- <img src="assets\img\topbs_background-image.jpg" alt=""> -->
            <div class="select-box">
                <el-radio-group v-model="attendeeType" class="radio-group">
                    <el-radio class="radio-item" value="1" border>Oversea Attendee</el-radio>
                    <el-radio class="radio-item" value="2" border>
                        <div class="domestic-radio">
                            <p>國內與會者</p>
                            <p>Domestic Attendee</p>
                        </div>
                    </el-radio>
                </el-radio-group>
                <nuxt-link class="next-btn" :to="`/registration-now/${attendeeType}`">
                    Next
                </nuxt-link>
            </div>
        </div>
    </main>
</template>

<script lang="ts" setup>
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue'
import Banner from '@/components/layout/Banner.vue';

useSeoMeta({
    title: 'Online Registration - 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery',
    description: 'Register online for the 9th IOPBS & TOPBS 2025 International Conference on Oncoplastic Breast Surgery. Choose your attendee type and proceed with the registration process.',
    keywords: 'Online Registration, IOPBS, TOPBS, 2025 Conference, Oncoplastic Breast Surgery'
})

const router = useRouter();

let attendeeType = ref('1');

const memberInfo = reactive({})

const getMemberInfo = async () => {
    let res = await CSRrequest.get('/member/getMemberInfo')
    if (res.code == 200) {
        console.log('getMemberInfo error', res);
        router.push('/member-center');
        ElMessage.success('Please log out before registering again');
        Object.assign(memberInfo, res.data);
        return;
    }
}

onMounted(() => {
    getMemberInfo();
});


</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;

    .title-section {
        margin-top: 1rem;
        text-align: center;
        position: relative;

        .title {
            font-size: 2.7rem;
            font-weight: 600;
        }

    }

    .select-section {
        background: url('assets/img/topbs_background-image.jpg') no-repeat center center;
        // width: 100vw;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 1.5rem;


        .select-box {
            background-color: white;
            border-radius: 15px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            box-shadow: 4px 3px 5px 1px rgba(0, 0, 0, 0.5);
            padding: 1.5rem;

            .radio-group {
                justify-content: center;
                padding: 1rem;
                gap: 1rem;

                .radio-item {
                    min-width: 18rem;
                    margin: 0 1rem;
                    padding: 2.5rem 2rem;
                    text-align: center;
                    display: flex;
                    justify-content: center;
                    border-radius: 15px;

                    .domestic-radio {
                        display: flex;
                        flex-direction: column;
                        align-items: center;
                        font-size: 1.3rem;
                        font-weight: 600;
                    }
                    font-weight: 600;

                    :deep(.el-radio__inner) {
                        border: #DE6A75 1px solid;

                        &::after {
                            background-color: #DE6A75;
                        }
                    }

                    :deep(.el-radio__label) {
                        font-size: 1.3rem;
                    }

                    &.is-checked {
                        border: 1px solid #DE6A75;

                        :deep(.el-radio__label) {
                            color: black;
                        }

                        :deep(.el-radio__inner) {
                            background-color: #DE6A75;
                            border: none;

                            &::after {
                                display: none;
                            }
                        }
                    }
                }
            }

            .next-btn {
                margin-top: 1.5rem;
                display: flex;
                justify-content: center;
                width: 30%;
                background-color: #DE6A75;
                color: white;
                border: none;
                border-radius: 10px;
                padding: 1.5rem 3rem;
                font-size: 1rem;
                font-weight: 500;

                &:hover {
                cursor: pointer;
                background-color: #fb7c88;
            }

            }
        }
    }
}
</style>