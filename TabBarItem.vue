<template>
  <div class="tab-bar-items" @click="itemClick">
<!--    <img src="../../assets/img/tabbar/1.png" alt="">
    <div>首页</div>-->
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>
  </div>

</template>

<script>
export default {
  name: "TabBarItem",
  props: {
    path: String,
    activeColor: {
      type: String,
      default: 'red'
    }
  },
  computed: {
    isActive() {
      return this.$route.path.indexOf(this.path) !== -1
    },
    activeStyle() {
      return this.isActive ? {color: this.activeColor} : {}
    }
  },
  methods: {
    itemClick() {
      this.$router.push(this.path)
    }
  }
}
</script>
  <style scoped>
  .tab-bar-items {
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }

  .tab-bar-items img {
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
  }

/*  .active {
    color: red;
  }*/
</style>
