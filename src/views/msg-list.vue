<template>
  <div
    id="mainBody"
    :style="{ height: this.$store.state.thisWindowHeight + 'px' }"
  >
    <div class="list-panel" style="outline: solid 1px black">
      列表显示
    </div>
    <div class="content-panel">
      <!--公用组件(消息展示)-->
      <router-view name="messageDisplay" />
    </div>
  </div>
</template>

<script>
export default {
  name: "msg-list",
  data() {
    return {
      msgSubscriptIco: require("../assets/img/msg-subscript.png"),
      avatarIco: require("../assets/img/avatar-ico.png"),
      groupMsgImg: require("../assets/img/group-msg-img.png"),
      GroupBlocked: require("../assets/img/Group_Blocked@2x.png"),
      otherMsgImg: require("../assets/img/other-msg-img.jpg")
    };
  }
};
</script>

<style lang="scss" scoped src="../assets/scss/msg-list.scss"></style>
