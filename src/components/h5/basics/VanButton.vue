<template>
  <el-button
    :type="myItem.propValues[typeIndex].value.chooseValue"
  
    >{{ myItem.propValues[titleIndex].value }}</el-button
  >
</template>
<script>
export default {
  props: {
    myItem: {},
  },

  data() {
    return {
      titleIndex: 0,
      typeIndex: 1,
      colorIndex: 2,
    };
  },
};
</script>
<style>
</style>