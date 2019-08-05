<template>
    <el-dialog 
        title="Preview" 
        :fullscreen="true"
        :visible.sync="dialogFormVisible">
        <div>
            <Row :key="index"
                v-for="(item,index) in rows"
                :rowIndex="index"
                :column="item"
            />
        </div>
    </el-dialog>
</template>
<script>
import Row from './SharedComponent/Row'
export default {
    components: {
        Row: {
            type:Object,
            required:true
        }
    },
    props: {
        visible: {
            type: Boolean,
            required: true
        },
        pageData: {
            type: Object,
            required: true
        }
    },
    computed: {
        rows() {
            console.log(this.pageData.rows)
            return this.pageData.rows
        }
    },
    data() {
        return {
            dialogFormVisible: false
        }
    },
    watch: {
        visible(val) {
            this.dialogFormVisible = val
        },
        dialogFormVisible(val){
            if(!val){
                this.$emit("close")
            }
        }
    }
}
</script>


