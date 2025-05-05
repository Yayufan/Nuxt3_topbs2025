<template>
    <main class="common-section">
        <Banner />
        <Breadcrumbs firstRoute="Member" secoundRoute="Abstract" />
        <Title title="Abstract" />

        <div class="paper-section">
            <div class="paper-table-box">
                <table class="paper-table">
                    <tr class="table-header">
                        <th v-if="isShowAll">Type</th>
                        <th>Title</th>
                        <th v-if="isShowAll">First Author</th>
                        <th>Action</th>
                    </tr>
                    <tr v-for="(paper, index) in paperList" :key="index"
                        :class="[index === paperList.length - 1 ? 'last-row' : '', isEvenOrOdd(index)]">
                        <td v-if="isShowAll" :class="isShowAll ? 'first-col' : ''">{{ paper.absType }}</td>
                        <td class="paper-title" :class="!isShowAll ? 'first-col' : ''">{{ paper.absTitle }}</td>
                        <td v-if="isShowAll">{{ paper.firstAuthor }}</td>
                        <td class="last-col">
                            <el-button link class="edit-btn" @click='headToEditPaper(paper)'>Edit</el-button>
                            <el-button link class="see-more-btn" @click='toggleSeeMore(paper)'>View</el-button>
                        </td>
                    </tr>
                </table>
            </div>
        </div>


        <el-dialog class="paper-info" v-model="isOpen" :width="dialogWidth">
            <table class="paper-info-table">
                <tr>
                    <td colspan="2" class="column-name title">Abstract</td>
                    <!-- <td>{{ paperInfo.paperId }}</td> -->
                </tr>
                <tr>
                    <td class="column-name">Type</td>
                    <td>{{ paperInfo.absType }}</td>
                </tr>
                <tr>
                    <td class="column-name">Abstract Title</td>
                    <td>{{ paperInfo.absTitle }}</td>
                </tr>
                <tr>
                    <td class="column-name">First Author</td>
                    <td>{{ paperInfo.firstAuthor }}</td>
                </tr>
                <tr>
                    <td class="column-name">First Author Birthday</td>
                    <td>{{ paperInfo.firstAuthorBirthday }}</td>
                </tr>
                <tr>
                    <td class="column-name">Speaker</td>
                    <td>{{ paperInfo.speaker }}</td>
                </tr>
                <tr>
                    <td class="column-name">Speaker Affillication</td>
                    <td>{{ paperInfo.speakerAffiliation }}</td>
                </tr>
                <tr>
                    <td class="column-name">CorrespondingAuthor</td>
                    <td>{{ paperInfo.correspondingAuthor }}</td>
                </tr>
                <tr>
                    <td class="column-name">CorrespondingAuthor Email</td>
                    <td>{{ paperInfo.correspondingAuthorEmail }}</td>
                </tr>
                <tr>
                    <td class="column-name">CorrespondingAuthor Phone</td>
                    <td>{{ paperInfo.correspondingAuthorPhone }}</td>
                </tr>
                <tr>
                    <td class="column-name">All Authors</td>
                    <td>{{ paperInfo.allAuthor }}</td>
                </tr>
                <tr>
                    <td class="column-name">All Authors Affiliation</td>
                    <td>{{ paperInfo.allAuthorAffiliation }}</td>
                </tr>
                <tr>
                    <td class="column-name">Abstract File</td>
                    <!-- <td><el-button @click="console.log(paperInfo.paperFileUpload)">click</el-button></td> -->
                    <td v-if="envMinio + paperInfo.FileUpload">
                        <a class="preview-link" :href="envMinio + paperInfo.paperFileUpload[0].path"
                            target="_blank">Preview</a>
                    </td>
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

const envMinio = useRuntimeConfig().public.minio
console.log(envMinio);

const isEvenOrOdd = (index: number) => {
    return index % 2 === 0 ? 'even' : 'odd'
}

const dialogWidth = ref('65%')
const isShowAll = ref(true);
const setShowAll = () => {
    if (window.innerWidth < 1024) {
        isShowAll.value = false; // 當視窗寬度小於 1024px 時，設置為 'top'
        dialogWidth.value = '90%'
    } else {
        isShowAll.value = true; // 否則設置為 'left'
        dialogWidth.value = '65%'
    }
    console.log(isShowAll.value)
}












/**------------------------------------------ */
onMounted(() => {
    getMemberInfo();
    getPapperList();
    window.addEventListener('resize', setShowAll);


})


</script>
<style lang="scss" scoped>
.common-section {
    font-family: $common-section-font-family;

    .paper-section {
        width: 100%;
        margin: 2rem auto;
        background: url('assets/img/topbs_background-image.jpg') center center;
        padding: 3rem 0;

    }

    .submit-btn {
        margin-left: 80%;
        margin-top: 20px;
    }

    .paper-table-box {
        width: 90%;
        background-color: white;
        margin: 0 auto;
        border-radius: 15px;
        padding: 1rem;

        .paper-table {
            width: 90%;
            margin: 0 auto;
            font-size: 1rem;
            // border-collapse: separate;
            border-spacing: 0;

            tr {

                th {
                    padding: 1rem;
                    text-align: left;
                    font-size: 1.3rem;
                    // border-bottom: 1px solid #ccc;
                }

                td {
                    padding: 1rem;
                    text-align: left;
                }

                .paper-title {
                    max-width: 20rem;
                    width: 20rem;
                    white-space: nowrap;
                    overflow: hidden;
                    text-overflow: ellipsis;
                }

            }

            .first-col {
                border-top-left-radius: 5px;
                border-bottom-left-radius: 5px;
            }

            .last-col {
                border-top-right-radius: 5px;
                border-bottom-right-radius: 5px;
                display: flex;
            }

            .even {
                td {
                    background-color: #E8979E;
                    color: white;
                    font-weight: bold;
                }

                .see-more-btn {
                    border: 1px solid white;
                    color: white;
                    padding: 0.3rem;
                    min-width: 3rem;

                    &:hover {
                        transform: scale(1.05);
                        transition: all 0.3s ease-in-out;
                    }
                }
                
                .edit-btn {
                    border: 1px solid white;
                    color: white;
                    padding: 0.3rem;
                    min-width: 3rem;

                    &:hover {
                        transform: scale(1.05);
                        transition: all 0.3s ease-in-out;
                    }
                }


            }

            .odd {
                td {
                    background-color: white;
                    color: #E8979E;
                    font-weight: bold;
                }
                
                .see-more-btn {
                    border: 1px solid #E8979E;
                    color: #E8979E;
                    padding: 0.3rem;
                    min-width: 3rem;
                    
                    &:hover {
                        transform: scale(1.05);
                        transition: all 0.3s ease-in-out;
                        color: black;
                    }
                }
                
                .edit-btn {
                    border: 1px solid #E8979E;
                    color: #E8979E;
                    padding: 0.3rem;
                    min-width: 3rem;
                    
                    &:hover {
                        color: black;
                        transform: scale(1.05);
                        transition: all 0.3s ease-in-out;
                    }
                }
            }

            // @media screen and (min-width: 1920px) {
            //     font-size: 1.5rem;
            // }



            @media screen and (max-width: 1023px) {
                font-size: 1rem;

                tr {

                    th {
                        font-size: 1.8rem;
                        padding: 0.5rem;
                        text-align: left;
                    }

                    td {
                        padding: 0.5rem;
                        text-align: left;
                    }

                    .paper-title {
                        max-width: 40rem !important;
                    }

                }

                .see-more-btn {
                    margin: 0;
                    min-width: 3rem;
                }

                .edit-btn {
                    margin: 0;
                    min-width: 3rem;
                }

                .last-col {
                    flex-direction: column;
                    align-items: flex-start;
                    gap: 0.5rem;
                }
            }

            @media screen and (max-width: 767px) {
                tr {
                    .paper-title {
                        max-width: 18rem !important;
                    }
                }

            }
        }


    }

    .paper-info {
        .paper-info-table {
            width: 100%;
            border: 1px solid #ccc;
            border-collapse: collapse;
            margin: 0 auto;
            font-size: 1.3rem;

            @media screen and (max-width: 1048px) {
                font-size: 1rem;
            }

            @media screen and (max-width: 368px) {
                font-size: 0.8rem;

            }

            tr {
                border: 1px solid #ccc;

                td {
                    padding: 1rem;
                    text-align: left;
                    border: 1px solid #ccc;
                }

                .column-name {
                    font-weight: bold;
                    background-color: #f2f2f2;
                    width: 30%;

                    @media screen and (max-width: 1048px) {
                        width: 20%;
                    }


                }

                .preview-link {
                    color: #007bff;
                    text-decoration: none;

                    &:hover {
                        text-decoration: underline;
                    }
                }

                .title {
                    font-size: 2rem;
                    font-weight: bold;
                    text-align: center;
                    background-color: #E8979E;
                    color: white;
                }
            }
        }

    }

}
</style>