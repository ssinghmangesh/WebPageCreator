<template>
    <div class="custom-page-board">
        <draggable v-model="rows">
                <Row :key="index"
                    v-for="(item,index) in rows"
                    :rowIndex="index"
                    :column="item"
                    @addDataInElement="addDataInElement"
                    @handleAddElement="handleAddElement"
                    draggable="true"
                    @drag="handleDrag" 
                    @drop="handleDrop"
                    @handleRemoveRow="handleRemoveRow"
                    @handleElementDrop="handleElementDrop"
                />
        </draggable>
    </div>
</template>
<script>
import draggable from 'vuedraggable'
import Row from './SharedComponent/Row'
export default { 
    components: {
        Row,
        draggable
    },
    props: {
        pageDetails: {
            type: Object,
            required: true
        }
    },
    mounted() {
        this.rows = this.pageDetails.rows
    },
    data() {
        return {
           rows: []
        }
    },
    computed: {
    },
    methods: {
        handleElementDrop(ep) {
            this.$emit("handleElementDrop",ep)
        },

        handleRemoveRow(val) {
            this.$emit("handleRemoveRow", val)
        },
        handleAddElement(elementPosition) {
            this.$emit("handleAddElement", elementPosition)
        },
        addDataInElement(elementPosition) {
            this.$emit("addDataInElement", elementPosition)
        },
        handleDrag($event) {
            console.log($event)
        },
        handleDrop($event) {
            console.log($event)
        }
    },
    watch: {
        rows(val) {
            this.$emit("dragDropPreformed", val)
        },
        pageDetails(val) {
            this.rows = val
        }
    }
    
}
</script>
<style>
.custom-page-board {
    padding: 20px;
    width: 100%;
    max-width: 1000px;
    margin: auto;
}

</style>


