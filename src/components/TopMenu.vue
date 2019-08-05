<template>
    <div class="custom-top-menu-group">

  <div class="custom-top-menu">
    <div>
      <el-tooltip class="item" effect="dark" content="Add Column" placement="top">
        <el-button @click="$emit('openAddRowModal')">
          <i class="el-icon-s-grid"></i>
        </el-button>
      </el-tooltip>
      
    </div>
  </div>
  <div class="custom-top-menu">

      <el-tooltip class="item" effect="dark" content="Drag this element to respected column" placement="top">
        <div
          draggable="true"
          @dragend="handleEvent('heading', $event)">
          H
        </div>
    </el-tooltip>
     <el-tooltip class="item" effect="dark" content="Drag this element to respected column" placement="top">
        <div
          draggable="true"
          @dragend="handleEvent('paragraph', $event)">
          P
        </div>
    </el-tooltip>
     <el-tooltip class="item" effect="dark" content="Drag this element to respected column" placement="top">
        <div
          draggable="true"
          @dragend="handleEvent('code', $event)">
         {{ 'code' }}
        </div>
    </el-tooltip>
     <el-tooltip class="item" effect="dark" content="Drag this element to respected column" placement="top">
        <div
          draggable="true"
          @dragend="handleEvent('image', $event)">
          <i class="el-icon-picture"></i>
        </div>
    </el-tooltip>
  </div>
      </div>
</template>
<script>
import TopMenuRightContent from "./TopMenuRightContent";
export default {
  components: {
    TopMenuRightContent
  },
  methods: {
    handleEvent(type,ev){
      this.$emit("dragItemType", type)
    }
  }
};
</script>
<style>
.custom-top-menu-group{
  display: flex;
}
.custom-top-menu {
  height: 70px;
  width: 100%;
  background-color: #ddeefe;
  padding-top: 15px;
  padding-left: 15px;
  padding-right: 15px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: center;
}
</style>

