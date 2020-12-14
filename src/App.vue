<template>
  <div class="App">
    <router-view></router-view>
  </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  name: 'App',
  data() {
    return {};
  },
  computed: {
    ...mapGetters(['getCounter'])
  },

  methods: {
    ...mapActions(['add'])
  }
};
</script>

<style lang="scss" scoped>
@import './assets/styles/var.scss';
.App {
  // text-align: center;
  // color: $primary-color;
  // font-size: 28px;
}
</style>