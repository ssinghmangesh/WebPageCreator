<template>
    <div class="custom-handle-handle">
    <div>
        <div class="custom-handle-handle-item">
            <div class="custom-handle-handle-item-title">List : </div>
            <div><el-input type="textarea" v-model="data"></el-input></div>
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
            data: ''
        }
    },
    methods: {
        onSubmit() {
            const { color, fontSize, padding, data } = this
            this.$emit("submited", {
                data
            })
        },
        onReset() { 
            this.data = ''
        }
    }
    
}
</script>
<style>
.custom-handle-handle {
    padding:20px;
}
</style>


