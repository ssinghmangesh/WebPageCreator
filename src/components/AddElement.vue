<template>
  <el-drawer title="Add Element" :visible.sync="visble" direction="rtl" size="50%">
    <div class="custom-add-row-body">
      <div class="custom-add-row-body-child" :key="index" v-for="(item, index) in rowsType">
        <div class="custom-add-row-element-container" @click="handleClick(item)">
          <div>{{ item }}</div>
        </div>
      </div>
    </div>
  </el-drawer>
</template>
<script>
export default {
  props: {
    open: {
      type: Boolean,
      required: true
    }
  },
  mounted() {
    this.visble = this.open;
  },
  data() {
    return {
      visble: false,
      rowsType: ["heading", "paragraph", "image", "code"]
    };
  },
  methods: {
    handleClick(element) {
      this.$emit("addElement", element);
      this.$emit("close");
    }
  },
  watch: {
    visble(val) {
      if (!val) {
        this.$emit("close");
      }
    },
    open(val) {
      this.visble = val;
    }
  }
};
</script>
<style>
.custom-add-row-body {
  width: 100%;
  display: flex;
  flex-wrap: wrap;
}
.custom-add-row-body-child {
  height: 160px;
  width: 50%;
  padding: 10px;
}
.custom-add-row-element-container {
  border: 1px solid;
  height: 100%;
  display: flex;
  align-items: center;
  flex-direction: column;
  justify-content: center;
  cursor: pointer;
}
</style>


