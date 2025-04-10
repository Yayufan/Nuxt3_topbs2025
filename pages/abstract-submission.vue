<template>
    <main class="common-section">
        <Breadcrumbs firstRoute="Abstracts" secoundRoute="Abstract Submission"></Breadcrumbs>
        <Title title="Abstract Submission"></Title>

        <el-form class="form" ref="formRef" :model="data" :rules="formRules">
            <el-form-item label="Abstract Type" prop="type">
                <el-select v-model="data.absType" placeholder="Type"></el-select>
            </el-form-item>
            <el-form-item label="Abstract Prop" prop="prop">
                <el-select v-model="data.absProp" placeholder="Prop"></el-select>
            </el-form-item>
            <el-form-item label="Abstract Title" prop="title">
                <el-input v-model="data.absTitle" placeholder="Titile"></el-input>
            </el-form-item>
            <el-form-item label="First Author" prop="firstAuthor">
                <el-input v-model="data.firstAuthor" placeholder="First Author"></el-input>
            </el-form-item>
            <el-form-item label="Speaker" prop="speaker">
                <el-input v-model="data.speaker" placeholder="Speaker"></el-input>
            </el-form-item>
            <el-form-item label="Speaker Affiliation" prop="speakerAffiliation">
                <el-input v-model="data.speakerAffiliation" placeholder="Speaker Affiliation"></el-input>
            </el-form-item>
            <el-form-item label="Corresponding Author" prop="correspondingAuthor">
                <el-input v-model="data.correspondingAuthor" placeholder="Corresponding Author"></el-input>
            </el-form-item>
            <el-form-item label="Corresponding Author Mail" prop="correspondingAuthorEmail">
                <el-input v-model="data.correspondingAuthorEmail" placeholder="Corresponding Author Email"></el-input>
            </el-form-item>
            <el-form-item label="Corresponding Author Phone" prop="correspondingAuthorPhone">
                <el-input v-model="data.correspondingAuthorPhone" placeholder="Corresponding Author Phone"></el-input>
            </el-form-item>
            <el-form-item label="All Authors" prop="allAuthors">
                <el-input v-model="data.allAuthor" placeholder="All Authors"></el-input>
            </el-form-item>
            <el-form-item label="All Authors Affiliation" prop="allAuthorsAffiliation">
                <el-input v-model="data.allAuthorAffiliation" placeholder="All Authors Affiliation"></el-input>
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
    </main>
</template>

<script lang="ts" setup>
import Banner from '@/components/layout/Banner.vue';
import Title from '@/components/layout/Title.vue';
import Breadcrumbs from '@/components/layout/Breadcrumbs.vue';

import type { FormInstance, FormRules, UploadProps, UploadUserFile, UploadFile, UploadFiles, UploadInstance } from 'element-plus';
import type { UseLinkOptions } from 'vue-router';


const router = useRouter();
/**-------------- Member info --------------- */
const memberInfo = reactive<any>({});

const getMemberInfo = async () => {
    let res = await CSRrequest.get('/member/getMemberInfo');

    if (res.code === 10002) {
        localStorage.removeItem("Authorization-member");
        router.push("/login");
    } else if (res.code === 200) {
        Object.assign(memberInfo, res.data);
        data.memberId = memberInfo.memberId;
    }
}

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
















const formRules = ref<FormRules>({})

const data = reactive<any>({
    absType: '1',
    absProp: '1',
    absTitle: '1',
    firstAuthor: '1',
    speaker: '1',
    speakerAffiliation: '1',
    correspondingAuthor: '1',
    correspondingAuthorEmail: '1',
    correspondingAuthorPhone: '1',
    allAuthor: '1',
    allAuthorAffiliation: '1',
})


const submitData = new FormData();
const submit = async () => {
    submitData.append('data', JSON.stringify(data));
    fileList.forEach((file: any) => {
        submitData.append('file', file.raw);
    })
    let res = await CSRrequest.post('/paper',{
        body: submitData
    });

    console.log(res);

}


onMounted(() => {
    getMemberInfo();
})

</script>