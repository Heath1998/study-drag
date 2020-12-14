<template>
  <div>
    <el-tabs tab-position="left">
      <el-tab-pane>
        <span slot="label"><i class="el-icon-s-grid"></i></span>
        <h5>视图树</h5>

      </el-tab-pane>
      <el-tab-pane>
        <span slot="label"><i class="el-icon-s-grid"></i></span>
        <h5>基础组件</h5>
        <draggable
          class="Compoent"
          :list="basicCompoents"
          :clone="cloneCompoents"
          :options="{
            sort: false,
          }"
          :group="{ name: 'components', pull: 'clone', put: false }"
        >
          <component-container
            v-for="(item, i) in basicCompoents"
            :key="i"
            :componentName="item.componentName"
            :name="item.name"
          >
          </component-container>
        </draggable>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import ComponentContainer from "@/components/h5/ComponentContainer.vue";
export default {
  components: {
    draggable,
    ComponentContainer
  },
  data() {
    return {
      basicCompoents: [
      {
        name: "按钮",
        id: "唯一值",
        componentName: "VanButton",
        mStyle: {},
        mClass: [],
        propValues: [
          {
            label: "标题",
            key: "title",
            value: "按钮",
            type: "text",
          },
          {
            label: "按钮类型",
            key: "type",
            type: "select",
            value: {
              chooseValue: "primary",
              data: [
                {
                  value: "primary",
                  label: "主要按钮",
                },
                {
                  value: "info",
                  label: "信息按钮",
                },
                {
                  value: "default",
                  label: "默认按钮",
                },
                {
                  value: "warning",
                  label: "警告按钮",
                },
                {
                  value: "danger",
                  label: "危险按钮",
                },
              ],
            },
          },
          {
            label: "按钮颜色",
            key: "color",
            type: "color",
            value: "#656262",
          },
        ],
      },
  ],
    }
  },
  computed: {
    globalId() {
      return this.$store.state.globalId;
    }
  },
  methods: {
    cloneCompoents: function (cloneObj) {
      let newObj = JSON.parse(JSON.stringify(cloneObj));
      this.$store.commit("globalIdInc");
      newObj.id = this.globalId;
      console.log(JSON.stringify(cloneObj));
      return newObj;
    },
  },
}
</script>

<style>

</style>