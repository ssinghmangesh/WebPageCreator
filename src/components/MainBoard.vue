<template>
  <div class="custom-main-board">
    <PageBoard 
        :pageDetails="pageDetails" 
        @handleAddElement="handleAddElement"
        @addDataInElement="addDataInElement"
        @handleRemoveRow="handleRemoveRow"
        @handleElementDrop="handleElementDrop"
        />
    <div class="custom-add-row-option">
      <div class="custom-add-row-option-container">
        <el-button @click="$emit('openAddRowModal')">ADD NEW ROW</el-button>
      </div>
    </div>
  </div>
</template>
<script>
import PageBoard from './PageBoard'
export default {
  components: {
    PageBoard
  },
  props: {
    pageDetails: {
      type: Object,
      required: true
    }
  },
    methods: {
        handleElementDrop(ep) {
            this.$emit("handleElementDrop",ep)
        },
        handleAddElement(elementPosition) {
            this.$emit("handleAddElement", elementPosition)
        },
        addDataInElement(elementPosition) {
            this.$emit("addDataInElement", elementPosition)
        },
        dragDropPreformed(data) {
            this.$emit("dragDropPreformed", data)
        },
        handleRemoveRow(val) {
            this.$emit("handleRemoveRow", val)
        },
    }
  
}
</script>
<style>

.custom-main-board {
  height: 100%;
  width: 100%;
  overflow: auto;
}
.custom-add-row-option {
  border: 1px solid;
  height: 130px;
  width: 100%;
  padding: 30px;
  border: 2px solid transparent;
  position: relative;
  transition: all 0.2s ease-in-out 0s;
  
}
.custom-add-row-option:hover {
  border: 2px solid #37ca37;
}
.custom-add-row-option-container{
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
    margin: 0 auto;
    border-radius: 4px;
    background: rgba(24,139,246,0.1);
    border: 1px solid rgba(24,139,246,0.2);
    text-align: center;
    padding: 7px;
    transition: all 0.2s ease-in-out 0s;
    cursor: pointer;
}

</style>

