<template>
    <div class="custom-handle-handle">
    <div>
        <div>
            <div>List : </div>
            <div><el-input type="textarea" v-model="data"></el-input></div>
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
            color: '',
            data: '',
            fontSize: '',
            padding: ''
        }
    },
    methods: {
        onSubmit() {
            const { color, fontSize, padding, data } = this
            this.$emit("submited", {
                style: {
                    color, fontSize, padding
                },
                data
            })
        },
        onReset() { 
            this.color = '',
            this.data = '',
            this.fontSize = '',
            this.padding = ''
        }
    }
    
}
</script>
<style>
.custom-handle-handle {
    padding:20px;
}
</style>


