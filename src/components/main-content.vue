<template>
  <div id="main-content">
    <!--路由出口-->
    <div class="main-content-view">
      <router-view name="mainArea" />
    </div>
  </div>
</template>

<script>
export default {
  name: "main-content",
  data() {
    return {
      searchImg: "block",
      searchContent: "",
      addBackground: "#ffffff",
      leftIco: "none",
      messageIco: require("../assets/img/menu-message-normal@2x.png"),
      messageIcoActive: require("../assets/img/menu-message-down@2x.png"),
      contactIco: require("../assets/img/menu-contact-normal@2x.png"),
      contactIcoActive: require("../assets/img/menu-contact-down@2x.png"),
      moreIco: require("../assets/img/menu-more-normal@2x.png"),
      moreIcoActive: require("../assets/img/menu-more-down@2x.png")
    };
  },
  methods: {
    // 显示搜索图标
    showSearchImg: function() {
      // 判断当前输入框是否有数据
      if (this.isEmpty(this.searchContent)) {
        this.searchImg = "block";
      } else {
        this.searchImg = "none";
      }
    },
    // 隐藏搜索图标
    hideSearchImg: function() {
      this.searchImg = "none";
    },
    // 创建群聊
    createGroupChat: function(status) {
      if (status) {
        this.addBackground = "#E1E3E5";
      } else {
        this.addBackground = "#ffffff";
      }
    },
    // 显示左上角图标
    showLeftIco: function(status) {
      if (status) {
        this.leftIco = "block";
      } else {
        this.leftIco = "none";
      }
    },
    // 在线状态
    onlineStatus: function() {},
    // 非空判断
    isEmpty: str => {
      str = str.trim();
      return str === "" || str === null || typeof str === "undefined";
    }
  }
};
</script>

<style scoped lang="scss" src="../assets/scss/main-content.scss"></style>
