<template>
    <div class="custom-handle-handle">
    <div>
        <div class="custom-handle-handle-item">
            <div class="custom-handle-handle-item-title">URL : </div>
            <div><el-input v-model="data" placeholder="http://example.com/image.png"></el-input></div>
        </div> 
        <div class="custom-handle-handle-item">
            <div class="custom-handle-handle-item-title">height : </div>
            <div><el-input v-model="height" placeholder="example 100, 200"></el-input></div>
        </div> 
        <div class="custom-handle-handle-item">
            <div class="custom-handle-handle-item-title">width : </div>
            <div><el-input v-model="width" placeholder="example 100, 200"></el-input></div>
        </div> 
        <div class="custom-handle-handle-item">
            <el-button type="primary" @click="onSubmit">Create</el-button>
            <el-button @click="onReset">Cancel</el-button>
        </div>
    </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            width: '',
            height: '',
            data: '',
        }
    },
    methods: {
        onSubmit() {
            const { width, height, data } = this
            this.$emit("submited", {
                style: {
                    width, 
                    height
                },
                data
            })
        },
        onReset() { 
            this.height = '',
            this.data = '',
            this.fonwidthtSize = ''
        }
    }
    
}
</script>
<style>
.custom-handle-handle {
    padding:20px;
}
</style>


