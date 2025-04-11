<template>
    <div>
        <main class="common-section">
            <Banner />

            <div class="title-section">
                <h1 class="title">Registration Now</h1>
            </div>
            <el-form :model="formData" class="form" ref="form" :rules="formRules" labelPosition="top"
                require-asterisk-position="right" :show-message="true" :scroll-to-error="true">
                <el-form-item class="member-title required" :label="formLabel.title" prop="title" labelPosition="left"
                    labelWidth="auto">
                    <el-radio-group v-model="formData.title">
                        <el-radio value="Prof.">Prof.</el-radio>
                        <el-radio value="Dr.">Dr.</el-radio>
                        <el-radio value="Mr.">Mr.</el-radio>
                        <el-radio value="Ms.">Ms.</el-radio>
                    </el-radio-group>
                </el-form-item>
                <div class="main-form">
                    <div class="left-seciton">
                        <div class="member-name">
                            <el-form-item class="first-name required" :label="formLabel.firstName" prop="firstName">
                                <el-input v-model="formData.firstName"></el-input>
                            </el-form-item>
                            <el-form-item class="last-name required" :label="formLabel.lastName" prop="lastName">
                                <el-input v-model="formData.lastName"></el-input>
                            </el-form-item>
                        </div>
                        <el-form-item :label="formLabel.chineseName" :prop="attendeeType === '2' ? 'chineseName' : ''">
                            <el-input v-model="formData.chineseName"></el-input>
                        </el-form-item>
                        <el-form-item class="email required" :label="formLabel.email" prop="email">
                            <el-input v-model="formData.email" :placeholder="formLabel.email2" :prefixIcon="Message"></el-input>
                        </el-form-item>
                        <el-form-item class="required" :label="formLabel.password" prop="password">
                            <el-input v-model="formData.password" :placeholder="formLabel.password" :prefixIcon="Lock"
                                show-password></el-input>
                        </el-form-item>
                        <el-form-item class="required" :label="formLabel.confirmPassword" prop="confirmPassword">
                            <el-input v-model="formData.confirmPassword" :placeholder="formLabel.confirmPassword" :prefixIcon="Lock"
                                show-password></el-input>
                        </el-form-item>
                        <el-form-item class="required" :label="formLabel.affiliation" prop="affiliation">
                            <el-input v-model="formData.affiliation"></el-input>
                        </el-form-item>
                        <el-form-item class="required" :label="formLabel.jobTitle" prop="jobTitle">
                            <el-input v-model="formData.jobTitle"></el-input>
                        </el-form-item>

                    </div>
                    <div class="right-section">
                        <el-form-item :label="formLabel.idCard" prop="idCard">
                            <el-input v-model="formData.idCard"></el-input>
                        </el-form-item>
                        <el-form-item class="required" :label="formLabel.country" prop="country">
                            <el-select :disabled="attendeeType === '2'" v-model="formData.country"
                                placeholder="Select a Country or Location" filterable @change="cleanRemitAccount">
                                <el-option v-for="item in countries" :key="item" :label="item"
                                    :value="item"></el-option>
                            </el-select>
                        </el-form-item>
                        <el-form-item v-if="formData.country === 'Taiwan'" :label="formLabel.remitAccountLast5"
                            prop="remitAccountLast5">
                            <el-input v-model="formData.remitAccountLast5"></el-input>
                        </el-form-item>
                        <div class="member-phone required">
                            <el-form-item class="country-code" :label="formLabel.countryCode" prop="countryCode">
                                <div class="country-code-inner">
                                    <el-input :disabled="attendeeType === '2'" v-model="formData.countryCode"
                                        placeholder="Country Code"></el-input>
                                    <span>-</span>
                                </div>
                            </el-form-item>
                            <el-form-item  :class="attendeeType === '1'? 'oversea-phone-num' : 'domestic-phone-num'" :label="formLabel.phoneNum" prop="phoneNum">
                                <el-input v-model="formData.phoneNum"></el-input>
                            </el-form-item>
                        </div>
                        <el-form-item class="category required" :label="formLabel.category" prop="category">
                            <el-radio-group v-model="formData.category">
                                <el-radio :value="1">{{ formLabel.category1 }}</el-radio>
                                <el-radio :value="2">{{ formLabel.category2 }}</el-radio>
                                <el-radio :value="3">{{ formLabel.category3 }}</el-radio>
                            </el-radio-group>
                        </el-form-item>
                    </div>
                </div>
                <el-form-item class="captcha" prop="captcha">
                    <el-input v-model="formData.verificationCode" placeholder="Captcha"></el-input>
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

import type { FormInstance, FormRules } from 'element-plus'
import { Lock, Message } from '@element-plus/icons-vue'

import Banner from '@/components/layout/Banner.vue';

import countriesJson from '@/assets/data/countries.json'
import Category from '../education-surgery/[category].vue';
import { id } from 'element-plus/es/locale/index.mjs';

const countries = reactive(countriesJson);


const router = useRouter()

const attendeeType = useRoute().params.attendeeType

/**-------------------------------匯款帳號末5碼校驗----------------------------- */


const validateRemitAccount = (rule: any, value: string, callback: any) => {
    if (formData.country === 'Taiwan' && !value) {
        callback(new Error('請輸入匯款帳號末5碼'))
    } else if (formData.country === 'Taiwan' && value.length !== 5) {
        callback(new Error('匯款帳號末5碼必須為5碼'))
    }
    else {
        callback()
    }
}

const validateChineseName = (rule: any, value: string, callback: any) => {
    if (formData.country === 'Taiwan' && !value) {
        callback(new Error('請輸入中文姓名'))
    }
    else {
        callback()
    }
}

const cleanRemitAccount = () => {
    formData.remitAccountLast5 = ''
}

const codeMap: Record<string, number> = {
    A: 10,
    B: 11,
    C: 12,
    D: 13,
    E: 14,
    F: 15,
    G: 16,
    H: 17,
    I: 34,
    J: 18,
    K: 19,
    L: 20,
    M: 21,
    N: 22,
    O: 35,
    P: 23,
    Q: 24,
    R: 25,
    S: 26,
    T: 27,
    U: 28,
    V: 29,
    W: 32,
    X: 30,
    Y: 31,
    Z: 33,
};

const checkCkDigit = (rule: any, value: string, callback: any) => {

    if (attendeeType === '1') {
        if (!value) {
            return callback(new Error(formLabel.idCardValidate));
        } else {
            return callback();
        }
    } else {

        if (!/^[A-Z][0-9]{9}$/.test(value)) {
            callback({ valid: false, message: "身份證格式不正確" });
        }

        const placeCode = codeMap[value[0]];
        if (!placeCode) {
            callback({ valid: false, message: "首碼無效" });
        }

        const bodyCode = value.substring(1, 9);
        const lastCode = value[9];
        const calHead = (num: number): number =>
            Math.floor(num / 10) * 1 + (num % 10) * 9;
        const calBody = (code: string): number => {
            let sum = 0;
            for (let i = 0; i < code.length; i++) {
                sum += parseInt(code[i]) * (8 - i);
            }
            return sum;
        };
        const idSum =
            calHead(placeCode) + calBody(bodyCode) + parseInt(lastCode) * 1;
        const isValid = idSum % 10 === 0;
        if (!isValid) {
            callback({ valid: false, message: "身分證號不合法" });
        } else {
            callback();
        }
    }


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
    formData.verificationKey = captchaData.key
}

/**---------------------- */
const formLabel = reactive({
    title: 'Title',
    firstName: 'First Name',
    lastName: 'Last Name',
    email: 'ID: Primary E-mail',
    email2: 'E-mail',
    password: 'Password',
    confirmPassword: 'Confirm Password',
    chineseName: 'Chinese Name',
    affiliation: 'Affiliation',
    jobTitle: 'Job Title',
    country: 'Country',
    remitAccountLast5: 'Remit Account Last 5 Number',
    countryCode: 'Country Code',
    idCard: 'Passport Number',
    phoneNum: 'Phone Number',
    category: 'Category',
    verificationCode: 'Verification Code',
    titleValidate: 'Please select a title',
    firstNameValidate: 'Please input your first name',
    lastNameValidate: 'Please input your last name',
    chineseNameValidate: 'Please input your Chinese name',
    emailValidate: 'Please input your email',
    emailValidate2: 'Please input correct email',
    passwordValidate: 'Please input your password',
    confirmPasswordValidate: 'Please input your password again',
    confirmPasswordValidate2: 'The two passwords do not match',
    affiliationValidate: 'Please input your affiliation',
    jobTitleValidate: 'Please input your job title',
    idCardValidate: 'Please input your passport number',
    idCardValidate2: 'Please input correct passport number',
    countryValidate: 'Please select a country',
    countryCodeValidate: 'Please input your country code',
    phoneNumValidate: 'Please input your phone number',
    categoryValidate: 'Please select a category',
    remitAccountLast5Validate: 'Please input your remit account last 5 number',
    category1: 'Non-member',
    category2: 'Member',
    category3: 'Others(Trainee/Nurse/Reasearcher)'
})

watch(() => attendeeType, (value) => {
    if (value === '2') {
        formLabel.title = '稱謂'
        formLabel.firstName = '英文名'
        formLabel.lastName = '英文姓氏'
        formLabel.chineseName = '中文姓名'
        formLabel.email = '電子信箱'
        formLabel.email2 = '電子信箱'
        formLabel.password = '密碼'
        formLabel.confirmPassword = '確認密碼'
        formLabel.affiliation = '所屬機構'
        formLabel.jobTitle = '職稱'
        formLabel.idCard = '身分證字號'
        formLabel.country = '國家'
        formLabel.remitAccountLast5 = '匯款帳號末五碼'
        formLabel.countryCode = '國碼'
        formLabel.phoneNum = '手機號碼'
        formLabel.category = '類別'
        formLabel.titleValidate = '請選擇稱謂'
        formLabel.firstNameValidate = '請輸入英文名'
        formLabel.lastNameValidate = '請輸入英文姓氏'
        formLabel.chineseNameValidate = '請輸入中文姓名'
        formLabel.emailValidate = '請輸入電子信箱'
        formLabel.emailValidate2 = '請輸入正確格式的電子信箱'
        formLabel.passwordValidate = '請輸入密碼'
        formLabel.confirmPasswordValidate = '請再次輸入密碼'
        formLabel.confirmPasswordValidate2 = '兩次密碼不相符'
        formLabel.affiliationValidate = '請輸入所屬機構'
        formLabel.jobTitleValidate = '請輸入職稱'
        formLabel.idCardValidate = '請輸入身分證字號'
        formLabel.idCardValidate2 = '請輸入正確格式的身分證字號'
        formLabel.countryValidate = '請選擇國家'
        formLabel.countryCodeValidate = '請輸入國碼'
        formLabel.phoneNumValidate = '請輸入手機號碼'
        formLabel.categoryValidate = '請選擇類別'
        formLabel.remitAccountLast5Validate = '請輸入匯款帳號末五碼'
        // formLabel.category1 = '非會員'
        // formLabel.category2 = '會員'
        // formLabel.category3 = '其他(實習醫師/護理人員/研究人員)'
    }
}, { immediate: true })




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
    category: number,
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
    category: 1,
    verificationCode: '',
    verificationKey: ''
})

watch(() => attendeeType, (value) => {
    if (value === '2') {
        formData.country = 'Taiwan';
        formData.countryCode = '886';
    }
}, { immediate: true })

const vaildConfirmPassword = (rule: any, value: string, callback: any) => {

    if (!value) {
        callback(new Error(formLabel.confirmPasswordValidate))
    } else if (value !== formData.password) {
        callback(new Error(formLabel.confirmPasswordValidate2))
    } else {
        callback()
    }
}



const formRules = reactive<FormRules>({
    title: [{ required: true, message: formLabel.titleValidate, trigger: 'change' }],
    firstName: [{ required: true, message: formLabel.firstNameValidate, trigger: 'blur' }],
    lastName: [{ required: true, message: formLabel.lastNameValidate, trigger: 'blur' }],
    email: [{ required: true, message: formLabel.emailValidate, trigger: 'blur' }, { type: 'email', message: formLabel.emailValidate2, trigger: 'blur' }],
    password: [{ required: true, message: formLabel.passwordValidate, trigger: 'blur' }],
    chineseName: [{ required: true, message: formLabel.chineseNameValidate, trigger: 'blur' }],
    confirmPassword: [{ validator: vaildConfirmPassword, trigger: 'blur' }],
    affiliation: [{ required: true, message: formLabel.affiliationValidate, trigger: 'blur' }],
    jobTitle: [{ required: true, message: formLabel.jobTitleValidate, trigger: 'blur' }],
    idCard: [{ required: true, validator: checkCkDigit, trigger: 'blur' }],
    country: [{ required: true, message: formLabel.countryValidate, trigger: 'change' }],
    countryCode: [{ required: true, message: formLabel.countryCodeValidate, trigger: 'blur' }],
    phoneNum: [{ required: true, message: formLabel.phoneNumValidate, trigger: 'blur' }],
    category: [{ required: true, message: formLabel.categoryValidate, trigger: 'change' }],
    remitAccountLast5: [{ validator: validateRemitAccount, trigger: 'blur' }]
})



const submit = async (formEl: FormInstance | undefined) => {
    if (!formEl) return;
    // console.log(valid)
    formEl.validate(async (valid) => {
        if (valid) {
            console.log(formEl)
            formData.phone = formData.countryCode + '-' + formData.phoneNum
            let res = await CSRrequest.post('/member', {
                body: formData
            })

            console.log(res)
            if (res.code === 500) {
                getCaptcha()
                formData.verificationCode = ''
                ElMessage.error(res.msg)
            }

            if (res.data.isLogin) {
                localStorage.setItem(res.data.tokenName, 'Bearer ' + res.data.tokenValue);
                router.push('/member-center')
            }

            formEl.resetFields()
        } else {
            console.log('error submit!!')
            return false;
        }
    })
}





/**---------------------- */
onMounted(() => {
    // router.push('/demo-register')
    getCaptcha()
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

                    .oversea-phone-num {
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
                    .domestic-phone-num {
                        flex: 2;

                        :deep(.el-form-item__label) {
                            color: white;
                            position: relative;

                            &::after {
                                position: absolute;
                                content: '國碼+電話號碼';
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
                // width: 10%;
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
}
</style>