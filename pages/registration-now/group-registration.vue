<template>
    <div>
        <main class="common-section">
            <Banner />

            <div class="title-section">
                <h1 class="title">Registration Now</h1>
            </div>
            <el-form :model="returnData" class="form" ref="form" :rules="formRules" labelPosition="top"
                require-asterisk-position="right" :show-message="true" :scroll-to-error="true">
                <div class="member-list" v-for="(item, index) in returnData.groupMembers" :key="index">
                    <div class="top-section">
                        <h1>Member {{ index + 1 }} : <span v-if="index === 0" class="tips">*The first on the list must
                                be a main member</span></h1>
                        <el-button class="option-btn" v-if="returnData.groupMembers.length > 5"
                            @click="removeMember(index)">
                            Remove
                        </el-button>
                    </div>
                    <el-form-item class="member-title required" label="Title" :prop="'groupMembers.' + index + '.title'"
                        :rules="formRules.title" labelPosition="left" labelWidth="auto">
                        <el-radio-group v-model="item.title">
                            <el-radio value="Prof.">Prof.</el-radio>
                            <el-radio value="Dr.">Dr.</el-radio>
                            <el-radio value="Mr.">Mr.</el-radio>
                            <el-radio value="Ms.">Ms.</el-radio>
                        </el-radio-group>
                    </el-form-item>
                    <div class="main-form">
                        <div class="left-seciton">
                            <div class="member-name">
                                <el-form-item class="first-name required" label="First Name"
                                    :prop="'groupMembers.' + index + '.firstName'" :rules="formRules.firstName">
                                    <el-input v-model="item.firstName"></el-input>
                                </el-form-item>
                                <el-form-item class="last-name required" label="Last Name"
                                    :prop="'groupMembers.' + index + '.lastName'" :rules="formRules.lastName">
                                    <el-input v-model="item.lastName"></el-input>
                                </el-form-item>
                            </div>
                            <el-form-item label="ChineseName" prop="chineseName">
                                <el-input v-model="item.chineseName"></el-input>
                            </el-form-item>
                            <el-form-item class="email required" label="ID: Primary E-mail"
                                :prop="'groupMembers.' + index + '.email'" :rules="formRules.email">
                                <el-input v-model="item.email" placeholder="E-mail" :prefixIcon="Message"></el-input>
                            </el-form-item>
                            <el-form-item class="required" label="Password"
                                :prop="'groupMembers.' + index + '.password'" :rules="formRules.password">
                                <el-input v-model="item.password" placeholder="Password" :prefixIcon="Lock"
                                    show-password></el-input>
                            </el-form-item>
                            <el-form-item class="required" label="Confirm Password"
                                :prop="'groupMembers.' + index + '.confirmPassword'" :rules="formRules.confirmPassword">
                                <el-input v-model="item.confirmPassword" placeholder="Password" :prefixIcon="Lock"
                                    show-password></el-input>
                            </el-form-item>
                            <el-form-item class="required" label="Affiliation"
                                :prop="'groupMembers.' + index + '.affiliation'" :rules="formRules.affiliation">
                                <el-input v-model="item.affiliation"></el-input>
                            </el-form-item>
                            <el-form-item class="required" label="Job Title"
                                :prop="'groupMembers.' + index + '.jobTitle'" :rules="formRules.jobTitle">
                                <el-input v-model="item.jobTitle"></el-input>
                            </el-form-item>

                        </div>
                        <div class="right-section">
                            <el-form-item label="Passport Number" :prop="'groupMembers.' + index + '.idCard'"
                                :rules="formRules.idCard">
                                <el-input v-model="item.idCard" placeholder="Passport Number"></el-input>
                            </el-form-item>
                            <el-form-item class="required" label="Country" :prop="'groupMembers.' + index + '.country'"
                                :rules="formRules.country">
                                <el-select :disabled="attendeeType === '2'" v-model="item.country"
                                    placeholder="Select a Country or Location" filterable @change="cleanRemitAccount">
                                    <el-option v-for="item in countries" :key="item" :label="item"
                                        :value="item"></el-option>
                                </el-select>
                            </el-form-item>
                            <div class="member-phone required">
                                <el-form-item class="country-code" label="Phone"
                                    :prop="'groupMembers.' + index + '.countryCode'" :rules="formRules.countryCode">
                                    <div class="country-code-inner">
                                        <el-input :disabled="attendeeType === '2'" v-model="item.countryCode"
                                            placeholder="Country Code"></el-input>
                                        <span>-</span>
                                    </div>
                                </el-form-item>
                                <el-form-item class="phone-num" label="phoneNum"
                                    :prop="'groupMembers.' + index + '.phoneNum'" :rules="formRules.phoneNum">
                                    <el-input v-model="item.phoneNum"></el-input>
                                </el-form-item>
                            </div>
                            <el-form-item label="Food Preference">
                                <el-radio-group v-model="item.food">
                                    <el-radio value="葷">Non-Vegetarian</el-radio>
                                    <el-radio value="素">Vegetarian</el-radio>
                                </el-radio-group>
                            </el-form-item>
                            <el-form-item :label="'Dietary restrictions'">
                                <el-input v-model="item.foodTaboo"></el-input>
                            </el-form-item>
                            <el-form-item class="category required" label="Category"
                                :prop="'groupMembers.' + index + '.category'" :rules="formRules.category">
                                <el-radio-group v-model="item.category" @change="cleanCategoryExtra(item)">
                                    <el-radio :value="1">Member</el-radio>
                                    <el-form-item v-if="item.category === 1"  :prop="'groupMembers.' + index + '.categoryExtra'" :rules="formRules.categoryExtra">
                                        <el-select  v-model="item.categoryExtra"
                                            class="category-select">
                                            <el-option label="IOPBS" value="IOPBS"></el-option>
                                            <el-option label="JOPBS" value="JOPBS"></el-option>
                                        </el-select>
                                    </el-form-item>
                                    <el-radio :value="2">Others(Trainee/Nurse/Reasearcher)</el-radio>
                                    <el-radio :value="3">Non-member</el-radio>
                                </el-radio-group>
                            </el-form-item>
                        </div>
                    </div>
                    <el-divider></el-divider>

                </div>
                <el-button @click="addNewMember" class="option-btn">
                    Add new
                </el-button>
                <el-form-item class="captcha" prop="captcha">
                    <el-input v-model="returnData.verificationCode" placeholder="Captcha"></el-input>
                    <div class="captcha-img">
                        <img :src="captchaData.image" alt="captcha">
                        <el-button class="refresh-btn" @click="getCaptcha"><el-icon>
                                <ElIconRefreshRight />
                            </el-icon></el-button>
                    </div>
                </el-form-item>
                <el-form-item class="submit-btn">
                    <el-button type="primary" @click="submit(form)">Submit</el-button>
                </el-form-item>
            </el-form>
        </main>

    </div>
</template>

<script lang="ts" setup>

import { type FormInstance, type FormRules } from 'element-plus'
import { Lock, Message } from '@element-plus/icons-vue'

import Banner from '@/components/layout/Banner.vue';

import countriesJson from '@/assets/data/countries.json'

const countries = reactive(countriesJson);




const router = useRouter()

const attendeeType = useRoute().params.attendeeType

/**-------------------------------匯款帳號末5碼校驗----------------------------- */


const validateRemitAccount = (rule: any, value: string, callback: any) => {
    if (formData.country === 'Taiwan' && !value) {
        callback(new Error('Please input your remit account last 5 number'))
    } else if (formData.country === 'Taiwan' && value.length !== 5) {
        callback(new Error('Please input 5 numbers'))
    }
    else {
        callback()
    }
}

const cleanRemitAccount = () => {
    formData.remitAccountLast5 = ''
}



/**-------------------------------取得驗證碼----------------------------- */

const captcha = ref('')
const captchaData = reactive({
    image: '',
    key: ''
})


const getCaptcha = async () => {
    console.log('getCaptcha')
    let res = await CSRrequest.get('/member/captcha')
    console.log(res)
    Object.assign(captchaData, res.data)
    returnData.verificationKey = captchaData.key
}




/**-------------------------------表單區塊----------------------------- */
interface formData {
    title: string,
    firstName: string,
    lastName: string,
    chineseName: string,
    email: string,
    password: string,
    confirmPassword: string,
    affiliation: string,
    jobTitle: string,
    country: string,
    idCard: string,
    remitAccountLast5: string,
    phone: string,
    countryCode: string,
    phoneNum: string,
    food: string,
    foodTaboo: string,
    category: number,
    categoryExtra: string,
    verificationCode: string,
    verificationKey: string
}

const form = ref<FormInstance>()

const formData = reactive<formData>({
    title: 'Prof.',
    firstName: '',
    lastName: '',
    chineseName: '',
    email: '',
    password: '',
    confirmPassword: '',
    affiliation: '',
    jobTitle: '',
    idCard: '',
    country: '',
    remitAccountLast5: '',
    phone: '',
    countryCode: '',
    phoneNum: '',
    food: '葷',
    foodTaboo: '',
    category: 1,
    categoryExtra: '',
    verificationCode: '',
    verificationKey: ''
})

const cleanCategoryExtra = (item: any) => {
    item.categoryExtra = ''
}

const returnData = reactive<any>({
    groupMembers: [],
    verificationCode: '',
    verificationKey: ''
})

const initMember = () => {
    returnData.groupMembers =
        Array.from({ length: 5 }, () => ({ ...formData }))
}

const addNewMember = () => {
    returnData.groupMembers.push({ ...formData })
}

const removeMember = (index: number) => {
    returnData.groupMembers.splice(index, 1)
}

watch(() => attendeeType, (value) => {
    if (value === '2') {
        formData.country = 'Taiwan';
        formData.countryCode = '886';
    }
}, { immediate: true })

const vaildConfirmPassword = (rule: any, value: string, callback: any) => {
    const match = rule.field.match(/^groupMembers\.(\d+)\.confirmPassword$/);
    if (!match) {
        return callback(new Error('Invalid field'));
    }

    const index = Number(match[1]); // 轉換為數字索引
    if (!value) {
        callback(new Error('Please input your password again'))
    } else if (value !== returnData.groupMembers[index].password) {
        callback(new Error('The two passwords do not match'))
    } else {
        callback()
    }
}

const validCategoryExtra = (rule: any, value: string, callback: any) => {
    const match = rule.field.match(/^groupMembers\.(\d+)\.categoryExtra$/);
    if (!match) {
        return callback(new Error('Invalid field'));
    }

    const index = Number(match[1]); // Convert to numeric index
    if (returnData.groupMembers[index].category === 1 && !value) {
        callback(new Error('Please select a category'));
    } else {
        callback();
    }
    
}



const formRules = reactive<FormRules>({
    title: [{ required: true, message: 'Please select a title', trigger: 'change' }],
    firstName: [{ required: true, message: 'Please input your first name', trigger: 'blur' }],
    lastName: [{ required: true, message: 'Please input your last name', trigger: 'blur' }],
    email: [{ required: true, message: 'Please input your email', trigger: 'blur' }, { type: 'email', message: 'Please input correct email', trigger: 'blur' }],
    idCard: [{ required: true, message: 'Please input your passport number', trigger: 'blur' }],
    password: [{ required: true, message: 'Please input your password', trigger: 'blur' }],
    confirmPassword: [{ validator: vaildConfirmPassword, trigger: 'blur' }],
    affiliation: [{ required: true, message: 'Please input your affiliation', trigger: 'blur' }],
    jobTitle: [{ required: true, message: 'Please input your job title', trigger: 'blur' }],
    country: [{ required: true, message: 'Please select a country', trigger: 'change' }],
    countryCode: [{ required: true, message: 'Please input your country code', trigger: 'blur' }],
    phoneNum: [{ required: true, message: 'Please input your phone number', trigger: 'blur' }],
    category: [{ required: true, message: 'Please select a category', trigger: 'change' }],
    remitAccountLast5: [{ validator: validateRemitAccount, trigger: 'blur' }],
    categoryExtra: [{ validator: validCategoryExtra, trigger: 'change' }],
})



const submit = async (formEl: FormInstance | undefined) => {
    if (!formEl) return;
    formEl.validate(async (valid) => {
        if (valid) {
            returnData.groupMembers.forEach((item: any) => {
                item.phone = item.countryCode + '-' + item.phoneNum
            })
            console.log(returnData)
            let res = await CSRrequest.post('/member/group', {
                body: returnData
            })

            if (res.code === 500) {
                getCaptcha()
                formData.verificationCode = ''
                ElMessage.error(res.msg)
            }

            if (res.code === 200) {
                router.push('/login')
                formEl.resetFields()
            }

        } else {
            console.log('error submit!!')
            return false;
        }
    })
}

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


/**---------------------- */
onMounted(() => {
    getCaptcha()
    initMember()
    getMemberInfo();
})
</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;

    .banner-box {
        margin-top: 1rem;

        img {
            width: 100%;
            box-shadow: 0px 6px 10px 0px rgba(0, 0, 0, 0.5);
        }
    }

    .title-section {
        margin: 1rem auto;
        text-align: center;

        .title {
            font-size: 2.7rem;
            font-weight: 600;
        }
    }


    .content {
        margin: 1rem auto;
        text-align: center;

        h1 {
            font-size: 2rem;
        }
    }

    .form {
        width: 80%;
        margin: 1rem auto;
        font-weight: 600;

        .option-btn {
            color: #DD6777;
            border: 1px solid #DD6777;
            border-radius: 5px;

            &:hover {
                color: white;
                background-color: #DD6777;
            }
        }

        .top-section {
            display: flex;
            justify-content: space-between;

            .tips {
                color: red;
            }
        }

        .member-title {
            display: flex;
            align-items: center;

            :deep(.el-form-item__label) {
                margin: 0 1rem 0 0;
                text-align: center;
            }
        }

        .main-form {
            display: flex;
            gap: 5rem;
            text-wrap: nowrap;

            @media screen and (max-width: 768px) {
                flex-direction: column;
                gap: 2rem;

            }


            .left-seciton {
                flex: 1;
                display: flex;
                flex-direction: column;


                .member-name {
                    display: flex;
                    justify-content: space-between;

                    .first-name {
                        flex: 1;
                        margin-right: 1rem;
                    }

                    .last-name {
                        flex: 1;
                    }
                }


            }

            .right-section {
                flex: 1;
                display: flex;
                flex-direction: column;

                .member-phone {
                    display: flex;
                    gap: 2rem;

                    .country-code {
                        flex: 1;

                        .country-code-inner {
                            display: flex;
                            align-items: center;
                            gap: 2rem;

                            :deep(.el-input) {
                                flex: 2;
                            }
                        }

                    }

                    .phone-num {
                        flex: 2;

                        :deep(.el-form-item__label) {
                            color: white;
                            position: relative;

                            &::after {
                                position: absolute;
                                content: 'Country Code+number';
                                color: red;
                                font-size: 0.7rem;
                                right: 0;
                            }
                        }
                    }
                }

                .category {

                    :deep(.el-radio-group) {
                        flex-direction: column;
                        display: flex;
                        justify-content: flex-start;
                        align-items: flex-start;
                    }

                    :deep(.el-form-item__error) {
                        // color: black;
                        position: absolute;
                        top: 0.5rem;
                        left: 10rem;
                        @media screen and (max-width: 768px) {
                            left: 13rem;
                        }
                    }

                    :deep(.el-select) {
                        width: 150px;
                    }
                }

            }

        }

        .captcha {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 1rem;
            margin: 0 auto;
            width: 80%;

            :deep(.el-form-item__content) {
                display: flex;
                justify-content: center;
                gap: 1rem;

                @media screen and (max-width: 768px) {
                    flex-direction: column;
                    gap: 1rem;

                }
            }

            :deep(.el-input) {
                width: 10rem;
            }

            .captcha-img {
                display: flex;
                align-items: center;
                gap: 1rem;

                @media screen and (max-width: 768px) {
                    flex-direction: column;
                    gap: 1rem;

                }

                .refresh-btn {
                    border: none;
                    background-color: white;
                    font-size: 1.5rem;
                    color: #D86C7C;

                    &:hover {
                        background-color: white;
                        color: #D86C7C;
                    }
                }


                img {
                    width: 10rem;
                }
            }

        }

        .submit-btn {
            display: flex;
            justify-content: center;
            text-align: center;
            margin-top: 2rem;

            .el-button {
                margin: 0 auto;
                background-color: #DD6777;
                border: none;
                border-radius: 5px;
            }
        }
    }

    :deep(.el-input__wrapper) {
        border-radius: 10px;
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
}
</style>