<template>
    <div>
        <TopMenu 
            @openAddRowModal="aopenAddRowModal"
            @showPreview="showPreview"
            @dragItemType="dragItemType"
        />
        <MainBoard 
            :pageDetails="pageDetails"
            @openAddRowModal="aopenAddRowModal"
            @handleAddElement="handleAddElement"
            @addDataInElement="addDataInElement"
            @dragDropPreformed="dragDropPreformed"
            @handleRemoveRow="handleRemoveRow"
            @dragItemType="dragItemType"
            @handleElementDrop="handleElementDrop"

        />
        <AddRow 
            :open="openAddRowModal" 
            @addRow="addRow"
            @close="closeAddRow"
        />
        <AddElement 
            :open="openAddElementModal" 
            @addElement="addElement"
            @close="closeAddElement"
        />
        <AddElementDetails 
            :open="openElementRuleModal" 
            :element="selectedElement"
            @submited="submited"
            @close="openElementRuleModal = false"
        />
       <!-- <ShowPreview 
            :visible="openShowPreview"
            :pageData="pageDetails"
            @close="closeShowPreview"
        /> -->
    </div>
</template>
<script>
import Vue from 'vue';

import AddRow from "./AddRow";
import ShowPreview from "./ShowPreview";
import AddElement from "./AddElement";
import AddElementDetails from "./AddElementDetails";
import TopMenu from "./TopMenu";
import MainBoard from "./MainBoard";
export default {
    components: {
        TopMenu,
        MainBoard,
        AddRow,
        AddElement,
        AddElementDetails,
        ShowPreview
    },
    data() {
        return {
            openAddRowModal: false,
            openAddElementModal: false,
            openElementRuleModal: false,
            updatingElementPosition: {},
            openShowPreview: false,
            selectedElement: {},
            pageDetails: {
                numberOfRow: 0,
                rows: []
            },
            dropPosition: null,
            dropElementType:''
        }
    },
    methods: {
        handleElementDrop(ep){
            this.dropPosition = ep
        },
        dragItemType(type){
            if(this.dropPosition) {
                const { rowIndex, columnIndex  } = this.dropPosition
                Vue.set( this.pageDetails.rows[rowIndex].column[columnIndex],'type' , type)

            }
            this.dropPosition = null
        },

        handleRemoveRow(val) {
            let r = this.pageDetails.rows
            r.splice(val, 1)
            Vue.set( this.pageDetails,'rows' , r)
        },
        dragDropPreformed(data) {
            Vue.set( this.pageDetails,'rows' , data)
        },
        addRow(columnCount) {
            this.pageDetails.numberOfRow = this.pageDetails.numberOfRow + 1
            let column = []
            for (let index = 0; index < columnCount; index++){
                column.push({})
            }
            this.pageDetails.rows.push({
                columnCount,
                column
            })
        },
        addElement(elementType) {
            const { rowIndex, columnIndex } = this.updatingElementPosition
            Vue.set( this.pageDetails.rows[rowIndex].column[columnIndex],'type' , elementType)
        },
        handleAddElement(elementPosition) {
              this.updatingElementPosition = elementPosition
              this.openAddElementModal = true;
        },
        addDataInElement(elementPosition) {
            this.updatingElementPosition = elementPosition
            const { rowIndex, columnIndex } = elementPosition
            this.selectedElement = this.pageDetails.rows[rowIndex].column[columnIndex]
            this.openElementRuleModal = true;
        },
        closeAddRow() {
          this.openAddRowModal = false;
        },
        closeAddElement() {
          this.openAddElementModal = false;
        },
        aopenAddRowModal() {
          this.openAddRowModal = true;
        },
        submited(elementData) {
              const { rowIndex, columnIndex } = this.updatingElementPosition
              const { style, data } = elementData
              Vue.set( this.pageDetails.rows[rowIndex].column[columnIndex],'data' , data)
              Vue.set( this.pageDetails.rows[rowIndex].column[columnIndex],'style' , style)

        },
        showPreview() {
            console.log("show preview")
            this.openShowPreview = true
        },
        closeShowPreview() {
            this.openShowPreview = false
        }
    }
};
</script>


