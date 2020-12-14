<template>
  <div class="rightPanel">
    <div class="rightPanelItems">
      <div v-for="(item, i) in currentData.propValues" :key="i">
        <div v-if="item.type === 'text'">
          <el-row>
            <el-col :span="10">{{item.label}}</el-col>
            <el-col :span="14">
              <el-input v-model="item.value"></el-input>
            </el-col>
          </el-row>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  computed: {
    currentData() {
      let data = this.$store.getters.currentData;
      if (typeof data == 'undefined') {
        this.flag = false;
        return { propValues: [] };
      } else {
        this.flag = true;
      }
      console.log(data)
      return data;
    }
  }
}
</script>

<style scoped>
.rightPanel {
  background-color: #ffffff;
  width: 300px;
  height: calc(100vh - 60px);
  box-shadow: -2px 0px 4px 0px rgba(0, 0, 0, 0.1);
  overflow-x: hidden;
  overflow-y: scroll;
}
.rightPanelItems {
  padding: 20px;
  padding-left: 10px;
}
.el-row {
  margin-bottom: 15px;
  line-height: 40px;
}
.el-icon-remove-outline {
  color: rgb(199, 23, 23);
}
.el-icon-remove-outline:hover {
  color: red;
}
</style>