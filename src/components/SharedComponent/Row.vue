<template>
    <div class="custom-row-style">
        <div 
            :key="index" 
            v-for="(item, index) in element" 
            :style="columnStyle" 
            class="custom-row"
            @click="handleClick(item, index)"
        >
            <Column 
                :elementDetails="item"
                :columnIndex="index"
                @handleAddElement="handleAddElement"
            />
        </div>
        <div class="custom-row-delete"@click="handleRemoveRow"><i class="el-icon-close"></i></div>
    </div>
</template>
<script>
import Column from './Column'
export default {
    components: {
        Column,
    },
    props: {
        column: {
            type: Object,
            required: true
        },
        rowIndex: {
            type: Number,
            required: true
        }
    },
    mounted() {
        this.editableColumn = this.column
    },
    data() {
        return {
            editableColumn: {}
        }
    },
    computed: {
        element() {
            return this.column.column
        },
        columnStyle() {
            return {
                width: (100 / this.column.columnCount) + '%',
                padding: '15px'
            }
        }

    },
    methods: {
        handleClick(item, index) {
            if(item.type) {
                this.$emit("addDataInElement", {
                    rowIndex: this.rowIndex,
                    columnIndex: index
                })
            }
        },
        handleAddElement(elementPosition) {
            const { rowIndex } = this
            let ep = {
                ...elementPosition,
                rowIndex
            }
            
            this.$emit("handleAddElement", ep)
        },
        handleRemoveRow() {
            const { rowIndex } = this
            this.$emit("handleRemoveRow", rowIndex)
        }
    }
}
</script>
<style>
.custom-row {
    border: 1px solid #fff;

}
.custom-row-delete {
    position: absolute;
    top: 0px;
    right: 0px;
}
.custom-row:hover {
    border: 1px solid #37ca37;
}
.custom-row-style{
    display:flex;
    position:relative;
}
</style>


