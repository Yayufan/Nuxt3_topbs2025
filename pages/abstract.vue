<template>
    <main class="common-section">
        <Banner />
        <Breadcrumbs firstRoute="Member" secoundRoute="Abstract" />
        <Title title="Abstract" />

        <div class="paper-section">
            <div v-for="(item, index) in paperList" class="paper">
                <div class="not-editable">
                    <div class="show-section">
                        <span>Type :{{ item.absType }}</span>
                        <span>Prop : {{ item.absProp }}</span>
                        <span>Title : {{ item.absTitle }}</span>
                        <el-button @click="seeMore(index)">more</el-button>
                        <el-button :disabled="item.status !== 0" @click="toggleToEdit(item, index)">edit</el-button>
                    </div>
                    <div :class="[`hide-section${index}`, 'hide-section']">
                        <p>First Author: {{ item.firstAuthor }}</p>
                        <p>Speaker: {{ item.speaker }}></p>
                        <p>Speaker Affiliation: {{ item.speakerAffiliation }}></p>
                        <p>Corresponding Author: {{ item.correspondingAuthor }}></p>
                        <p>Corresponding Author Email: {{ item.correspondingAuthorEmail }}></p>
                        <p>Corresponding Author Phone: {{ item.correspondingAuthorPhone }}></p>
                        <p>All Authors: {{ item.allAuthor }}></p>
                        <p>All Authors Affiliation: {{ item.allAuthorAffiliation }}></p>
                        <p>File:</p>
                    </div>
                </div>

            </div>
        </div>

        <el-drawer v-model="isEdit">
            <el-form class="form" ref="formRef" :model="editPaper" :rules="formRules">
            <el-form-item label="Abstract Type" prop="type">
                <el-select v-model="editPaper.absType" placeholder="Type"></el-select>
            </el-form-item>
            <el-form-item label="Abstract Prop" prop="prop">
                <el-select v-model="editPaper.absProp" placeholder="Prop"></el-select>
            </el-form-item>
            <el-form-item label="Abstract Title" prop="title">
                <el-input v-model="editPaper.absTitle" placeholder="Titile"></el-input>
            </el-form-item>
            <el-form-item label="First Author" prop="firstAuthor">
                <el-input v-model="editPaper.firstAuthor" placeholder="First Author"></el-input>
            </el-form-item>
            <el-form-item label="Speaker" prop="speaker">
                <el-input v-model="editPaper.speaker" placeholder="Speaker"></el-input>
            </el-form-item>
            <el-form-item label="Speaker Affiliation" prop="speakerAffiliation">
                <el-input v-model="editPaper.speakerAffiliation" placeholder="Speaker Affiliation"></el-input>
            </el-form-item>
            <el-form-item label="Corresponding Author" prop="correspondingAuthor">
                <el-input v-model="editPaper.correspondingAuthor" placeholder="Corresponding Author"></el-input>
            </el-form-item>
            <el-form-item label="Corresponding Author Mail" prop="correspondingAuthorEmail">
                <el-input v-model="editPaper.correspondingAuthorEmail" placeholder="Corresponding Author Email"></el-input>
            </el-form-item>
            <el-form-item label="Corresponding Author Phone" prop="correspondingAuthorPhone">
                <el-input v-model="editPaper.correspondingAuthorPhone" placeholder="Corresponding Author Phone"></el-input>
            </el-form-item>
            <el-form-item label="All Authors" prop="allAuthors">
                <el-input v-model="editPaper.allAuthor" placeholder="All Authors"></el-input>
            </el-form-item>
            <el-form-item label="All Authors Affiliation" prop="allAuthorsAffiliation">
                <el-input v-model="editPaper.allAuthorAffiliation" placeholder="All Authors Affiliation"></el-input>
            </el-form-item>
            <el-form-item label="File" prop="file">
                <el-upload ref="uploadRef" class="upload-demo" :limit="1" :on-change="handlePdfUpload">
                    <el-button size="small" type="primary">Upload</el-button>
                    <div slot="tip" class="el-upload__tip">only upload pdf file with size less than 20mb</div>
                </el-upload>
            </el-form-item>
             <el-form-item label="File2" prop="file2">
                <el-upload ref="uploadRef1" class="upload-demo" :limit="1" :on-change="handleDocxUpload">
                    <el-button size="small" type="primary">Upload</el-button>
                    <div slot="tip" class="el-upload__tip">only upload word file with size less than 20mb</div>
                </el-upload>
            </el-form-item> 
            <el-form-item>
                <el-button type="primary" @click="submit">Submit</el-button>
            </el-form-item>
        </el-form>
        </el-drawer>
    </main>
</template>
<script lang="ts" setup>
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue';
import Title from '@/components/layout/Title.vue';
import Banner from '@/components/layout/Banner.vue';

import type { FormInstance, UploadUserFile, UploadProps } from 'element-plus';


const router = useRouter();
/**----------------------------------------- */
const memberInfo = reactive<any>({});
const getMemberInfo = async () => {
    let res = await CSRrequest.get('/member/getMemberInfo');
    if (res.code === 10002) {
        localStorage.removeItem('Authorization-member');
        router.push('/login');
    } else if (res.code === 200) {
        Object.assign(memberInfo, res.data);
        editPaper.memberId = memberInfo.memberId;
    }

}
/**------------------------------------------ */
const paperList = reactive<any>([]);
const getPapperList = async () => {
    let res = await CSRrequest.get('/paper/owner');
    Object.assign(paperList, res.data);
    console.log(res.data)
}

const seeMore = (index: number) => {
    let info = document.getElementsByClassName(`hide-section${index}`);
    if (info) {
        info[0].classList.toggle('hide-section');
    }
}

const editPaper = reactive<any>({});
const isEdit = ref(false);
const toggleToEdit = (paper: any, index: number) => {
    editPaper.absType = paper.absType;
    editPaper.absProp = paper.absProp;
    editPaper.absTitle = paper.absTitle;
    editPaper.firstAuthor = paper.firstAuthor;
    editPaper.speaker = paper.speaker;
    editPaper.speakerAffiliation = paper.speakerAffiliation;
    editPaper.correspondingAuthor = paper.correspondingAuthor;
    editPaper.correspondingAuthorEmail = paper.correspondingAuthorEmail;
    editPaper.correspondingAuthorPhone = paper.correspondingAuthorPhone;
    editPaper.allAuthor = paper.allAuthor;
    editPaper.allAuthorAffiliation = paper.allAuthorAffiliation;
    editPaper.paperId = paper.paperId;
    isEdit.value = !isEdit.value;
    console.log(editPaper)
   
}

const formRules = ref<FormInstance>();

/**------------------------------------------ */
const checkFileSize = (size: number) => {
    return size < 1024 * 1024 * 20;
}

const fileList = reactive<UploadUserFile[]>([]);

const handlePdfUpload: UploadProps['onChange'] = (file: UploadUserFile, uploadFiles) => {
    if (file.size == 0) {
        ElMessage.error('File is empty');
        return false;
    }
    
    
    if (file.status === 'success' && file.size) {
        if (!checkFileSize(file.size)) {
            ElMessage.error('File size must be less than 20mb');
            uploadFiles.pop();
            return;
        }
        if (file.name.split('.').pop() !== 'pdf') {
            ElMessage.error('File must be pdf');
            uploadFiles.pop();
            return;
        }
        fileList.push(file);
    }

}
const handleDocxUpload: UploadProps['onChange'] = (file: UploadUserFile, uploadFiles) => {
    if (file.size == 0) {
        ElMessage.error('File is empty');
        return false;
    }
    
    
    if (file.status === 'success' && file.size) {
        if (!checkFileSize(file.size)) {
            ElMessage.error('File size must be less than 20mb');
            uploadFiles.pop();
            return;
        }
        if (file.name.split('.').pop() !== 'docx') {
            ElMessage.error('File must be docx');
            uploadFiles.pop();
            return;
        }
        fileList.push(file);
    }

}

watch(fileList, (newVal) => {
    console.log(newVal);
}, { deep: true })

const submitData = new FormData();
const submit = async () => {
    submitData.append('data', JSON.stringify(editPaper));
    fileList.forEach((file: any) => {
        submitData.append('file', file.raw);
    })
    let res = await CSRrequest.put('/paper/owner',{
        body: submitData
    });

    console.log(res);

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
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;

        .paper {
            border: 1px solid #d7d7d7;

            .show-section {
                display: flex;
                justify-content: space-between;
                padding: 10px;
                border-bottom: 1px solid #d7d7d7;
            }

            .hide-section {
                display: none;
            }

            .editable {
                display: none;
            }
        }
    }
}
</style>