<template>
  <div class="custom-top-menu">
    <div>
      <el-tooltip class="item" effect="dark" content="Add Column" placement="top">
        <el-button @click="$emit('openAddRowModal')">
          <i class="el-icon-s-grid"></i>
        </el-button>
      </el-tooltip>
      <el-tooltip class="item" effect="dark" content="Add Element" placement="top">
        <el-button>
          <i class="el-icon-document-add"></i>
        </el-button>
      </el-tooltip>
    </div>
  </div>
</template>
<script>
import TopMenuRightContent from "./TopMenuRightContent";
export default {
  components: {
    TopMenuRightContent
  }
};
</script>
<style>
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

