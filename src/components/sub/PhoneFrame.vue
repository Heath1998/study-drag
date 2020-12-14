<template>
  <div class="phone-s">
    <div class="phone">
      <draggable
        :list="list"
        group="components"
        class="draggableDiv"
      >
        <div
          v-for="(item, i) in list"
          :key="i"
          class="content"
        >

        <component
          @click.native="switchIndex(i)"
          class="hoverborder"
          :is="item.componentName"
          :myItem="item"
        ></component>
        </div>
      </draggable>
    </div>
  </div>
</template>

<script>
import draggable from 'vuedraggable';
import basicsMixin from "@/js/h5/importBasics";

export default {
  mixins: [basicsMixin],
  components: {
    draggable
  },
  data() {
    return {
      one:[]
    }
  },
  computed: {
    list() {
      console.log(this.$store.state.list)
      return this.$store.state.list;
    },
    animateClass() {
      return this.$store.state.rightPanelClass.animateClass;
    },
  },
  methods: {
    switchIndex(index) {
      if (this.animateClass === 'myBounceOutRight') {
        this.$store.commit('rightPanelFold');
      }
      this.$store.commit('switchIndex', index)
    }
  }
}
</script>


<style lang="scss" scoped>
$phoneWidth: 375px;
$phoneHeight: 667px;

.draggableDiv {
  position: absolute; 
  top: 25px; 
  bottom: 0; 
  left: 0; 
  right: 0;
  // display:flex;
  // flex-wrap: wrap;
  // align-items: flex-start;
  // align-content: flex-start;
}
.phone-s {
  width: $phoneWidth;
  height: $phoneHeight;
  position: relative;
  margin-left: auto;
  margin-right: auto;
}
.phone {
  width: $phoneWidth;
  height: $phoneHeight;
  background-color: white;
  position: relative;
  margin-left: auto;
  margin-right: auto;
  overflow-x: hidden;
}
.hoverborder {
  border: 1px solid transparent;
}
.hoverborder:hover {
  border: 1px solid blue;
}
.content{
  padding: 1px;
}
</style>