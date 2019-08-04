<template>
  <el-drawer title="Elements Rule Defination" :visible.sync="visble" direction="rtl" size="50%">
    <div>
      <Handle :elementData="element"
        @submited="submited"/>
    </div>
  </el-drawer>
</template>
<script>
import Handle from './SharedComponent/ElementHandle'
export default {
  components: {
    Handle
  },
  props: {
    open: {
      type: Boolean,
      required: true
    },
    element: {
      type: Object,
      required: true
    }
  },
  mounted() {
    this.visble = this.open;
  },
  data() {
    return {
      visble: false,
    };
  },
  methods: {
    handleClick(element) {
    },
    submited(data){
      this.$emit("submited", data)
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
</style>


