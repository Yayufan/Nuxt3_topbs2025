<template>
    
</template>
<script setup lang="ts">
    const returnEcPay = async () => {
        let res = await CSRrequest.post(`/payment`)
    }

    onMounted(()=> {
        returnEcPay()
    })
</script>