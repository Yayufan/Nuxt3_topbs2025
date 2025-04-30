<template>
    <main class="common-section">
        <Banner />
        <Breadcrumbs firstRoute="Member" secoundRoute="Abstract" />
        <Title title="Abstract" />

        <div class="paper-section">
            <el-table :data="paperList" border stripe style="width: 100%">
                <el-table-column prop="absType" label="Type" width="180"></el-table-column>
                <el-table-column prop="absTitle" label="Abstract Title"></el-table-column>
                <el-table-column prop="firstAuthor" label="First Author" width="180"></el-table-column>
                <el-table-column align='center' label='Action'>
                    <template #default="{ row, $index }">
                        <el-button link type="primary" @click='headToEditPaper(row)'>Edit</el-button>
                        <el-button type="success" link @click='toggleSeeMore(row)'>See More</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </div>


        <el-dialog class="paper-info" v-model="isOpen" title="Abstract" width="65%">
            <table>
                <tr>
                    <td>Type</td>
                    <td>{{ paperInfo.absType }}</td>
                </tr>
                <tr>
                    <td>Abstract ID</td>
                    <td>{{ paperInfo.paperId }}</td>
                </tr>
                <tr>
                    <td>Abstract Title</td>
                    <td>{{ paperInfo.absTitle }}</td>
                </tr>
                <tr>
                    <td>First Author</td>
                    <td>{{ paperInfo.firstAuthor }}</td>
                </tr>
                <tr>
                    <td>First Author Birthday</td>
                    <td>{{ paperInfo.firstAuthorBirthday }}</td>
                </tr>
            </table>
        </el-dialog>
    </main>
</template>
<script lang="ts" setup>
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue';
import Title from '@/components/layout/Title.vue';
import Banner from '@/components/layout/Banner.vue';

import type { FormInstance, FormRules, UploadUserFile, UploadProps, UploadInstance } from 'element-plus';


const router = useRouter();
/**----------------------------------------- */
const memberInfo = reactive<any>({});
const getMemberInfo = async () => {
    let res = await CSRrequest.get('/member/getMemberInfo');
    if (res.code === 200) {
        Object.assign(memberInfo, res.data);
    } else {
        localStorage.removeItem('Authorization-member');
        router.push('/login');
    }
}
/**------------------------------------------ */
const paperList = reactive<any>([]);
const getPapperList = async () => {
    let res = await CSRrequest.get('/paper/owner');
    Object.assign(paperList, res.data);
    console.log(res.data)
}
/**------------------------------------------ */


const headToEditPaper = (paper: any) => {
    router.push(`/abstract-item/${paper.paperId}`)
}

const isOpen = ref(false);
const paperInfo = ref<any>({});
const toggleSeeMore = (paper: any) => {
    isOpen.value = true;
    console.log(paper);

    Object.assign(paperInfo.value, paper);
}










/**------------------------------------------ */
onMounted(() => {
    getMemberInfo();
    getPapperList();

})


</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;

    .paper-section {
        width: 80%;
        margin: 2rem auto;
    }

    .submit-btn {
        margin-left: 80%;
        margin-top: 20px;
    }


    .paper-info {
        background-color: $accent-color;
        border-radius: 15px ;
    }

    .form {
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
        }

        .right-section {
            flex: 1;
            display: flex;
            flex-direction: column;


            .el-input {
                width: 200px;
            }

            .el-textarea {
                width: 200px;
            }
        }
    }

}
</style>