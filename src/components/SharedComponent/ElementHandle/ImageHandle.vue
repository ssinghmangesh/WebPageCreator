<template>
    <div class="custom-handle-handle">
    <div>
        <div>
            <div>URL : </div>
            <div><el-input v-model="data"></el-input></div>
        </div> 
        <div>
            <div>height : </div>
            <div><el-input v-model="height"></el-input></div>
        </div> 
        <div>
            <div>width : </div>
            <div><el-input v-model="width"></el-input></div>
        </div> 
        <div>
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


