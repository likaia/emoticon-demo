<template>
  <div id="mainContent">
    <div class="top-panel"></div>
    <!--消息显示-->
    <div class="messages-panel">
      <div class="row-panel"></div>
      <div class="row-panel"></div>
      <div class="row-panel"></div>
    </div>

    <!--用户输入模块-->
    <div class="user-input-panel">
      <div class="toolbar-panel">
        <div class="item-panel">
          <img
            :src="resourceObj.toolbarBarIco.emoticon"
            @mouseenter="displayExpression('hover')"
            @mouseleave="displayExpression('leave')"
            @mousedown="displayExpression('down')"
            @mouseup="displayExpression('up')"
            alt=""
          />
        </div>
      </div>
      <div class="input-panel">
        <textarea
          @keydown.enter.exact="sendMessage($event)"
          v-model="messageContent"
        ></textarea>
      </div>
      <!--表情面板-->
      <div class="emoticon-panel" style="border: solid 1px red"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "message-display",
  data() {
    return {
      userId: this.$route.params.userId,
      createDisSrc: require("../assets/img/titlebar_function_createDis_normal@2x.png"),
      resourceObj: {
        createDisNormal: require("../assets/img/titlebar_function_createDis_normal@2x.png"),
        createDisHover: require("../assets/img/titlebar_function_createDis_hover@2x.png"),
        createDisClick: require("../assets/img/titlebar_function_createDis_normal_p@2x.png"),
        phoneNormal: require("../assets/img/phone_normal_ap@2x.png"),
        groupMsgImg: require("../assets/img/group-msg-img.png"),
        avatarImg: require("../assets/img/avatar.jpg"),
        msgImgTest: require("../assets/img/msg-img-test.gif"),
        msgImgTestB: require("../assets/img/msg-img-testB.gif"),
        toolbarBarIco: {
          emoticon: require("../assets/img/toolbar_emoticon_normal@2x.png"),
          emoticonNormal: require("../assets/img/toolbar_emoticon_normal@2x.png"),
          emoticonHover: require("../assets/img/toolbar_emoticon_hover@2x.png"),
          emoticonDown: require("../assets/img/toolbar_emoticon_down@2x.png"),
          screenCaptureNormal: require("../assets/img/toolbar_screenCapture_normal@2x.png"),
          screenCaptureHover: require("../assets/img/toolbar_screenCapture_hover@2x.png"),
          screenCaptureDown: require("../assets/img/toolbar_screenCapture_down@2x.png"),
          filesNormal: require("../assets/img/toolbar_files_normal@2x.png"),
          filesHover: require("../assets/img/toolbar_files_hover@2x.png"),
          filesDown: require("../assets/img/toolbar_files_down@2x.png"),
          phoneNormal: require("../assets/img/toolbar_phone_normal@2x.png"),
          phoneHover: require("../assets/img/toolbar_phone_hover@2x.png"),
          phoneDown: require("../assets/img/toolbar_phone_down@2x.png"),
          historyNormal: require("../assets/img/toolbar_history_normal@2x.png"),
          historyHover: require("../assets/img/toolbar_history_hover@2x.png"),
          historyDown: require("../assets/img/toolbar_history_down@2x.png"),
          shakeNormal: require("../assets/img/toolbar_shake_normal@2x.png"),
          shakeHover: require("../assets/img/toolbar_shake_hover@2x.png"),
          shakeDown: require("../assets/img/toolbar_shake_down@2x.png")
        }
      },
      messageContent: "",
      InputContent: ""
    };
  },
  mounted: function() {},
  methods: {
    createDisEventFun: function(status) {
      if (status === "hover") {
        this.createDisSrc = this.resourceObj.createDisHover;
      } else if (status === "leave") {
        this.createDisSrc = this.resourceObj.createDisNormal;
      } else {
        this.createDisSrc = this.resourceObj.createDisClick;
      }
    },
    sendMessage: function(event) {
      if (event.keyCode === 13) {
        console.log("消息发送");
      }
    },
    // 显示表情
    displayExpression: function(status) {
      if (status === "hover" || status === "up") {
        this.resourceObj.toolbarBarIco.emoticon = this.resourceObj.toolbarBarIco.emoticonHover;
      } else if (status === "leave") {
        this.resourceObj.toolbarBarIco.emoticon = this.resourceObj.toolbarBarIco.emoticonNormal;
      } else {
        this.resourceObj.toolbarBarIco.emoticon = this.resourceObj.toolbarBarIco.emoticonDown;
      }
    }
  },
  beforeRouteUpdate(to, form, next) {
    // 路由更新改变当前userId
    this.userId = to.params.userId;
    next();
  }
};
</script>

<style lang="scss" src="../assets/scss/message-display.scss" scoped></style>
