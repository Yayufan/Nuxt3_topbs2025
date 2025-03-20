<template>
    <main class="common-section">
        <el-table :data="orderList" ref="orderListRef" >
            <el-table-column prop="ordersId" label="訂單編號"></el-table-column>
            <el-table-column>
                <template #default="scope">
                    <el-button @click="getOrders(scope.row.ordersId)">付款</el-button>
                </template>
            </el-table-column>


        </el-table>
        <div  v-html="form" ref="formRef"></div>
    </main>
</template>

<script lang="ts" setup>

    const orderListRef = ref<any>();
    

    let orderList = reactive<any>([])
    const getOrderListForOwner = async () => {
        let res = await CSRrequest.get('/orders/owner')
        Object.assign(orderList, res.data)
        console.log(orderList)
    }

    /**----------------------------前往付款------------------- */

    const formRef = ref<any>()

    const form = ref<any>()

    const getOrders = async (ordersId: number) => {
        console.log(ordersId)
        let res = await CSRrequest.get(`/orders/owner/${ordersId}`)
        console.log(res.data)
        res = await CSRrequest.get(`/orders/payment`, {
            params: {
                id: ordersId
            }
        })
        form.value = res.data

        await nextTick();
        if (formRef.value) {
            // console.log(formRef.value)
            // formRef.value.submit()
            const formItem = formRef.value.querySelector("form")
            console.log(formItem)
            formItem.submit()
        }



    }


    onMounted(() => {
        getOrderListForOwner()
    })
</script>