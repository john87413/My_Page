<template>
  <div class="footer-contact d-flex jc-center ai-center p-4">
    <!-- contact -->
    <div class="my-connect d-flex flex-column">
      <!-- title -->
      <P class="connect-title text-white fs-xxl m-0 my-3">My contacts</P>
      <!-- 內容 -->
      <div
        class="connect-info d-flex mt-4"
        v-for="(item, index) in connectInfo"
        :key="index"
      >
        <i
          class="iconfont fs-lg text-white mr-2"
          :class="`icon-${item.icon}`"
        ></i>
        <p class="m-0 mx-2 fs-lgs text-white">{{ item.text }}</p>
      </div>
    </div>
    <!-- comment -->
    <div class="send-comment d-flex flex-column ml-9">
      <!-- title -->
      <p class="text-white fs-xxl my-3">{{ comment.title }}</p>
      <!-- form -->
      <textarea
        class="bg-none fs-lg text-white py-1 px-2 my-1"
        v-for="(item, index) in comment.commentList"
        v-model="item.text"
        :key="index"
        :placeholder="item.place"
      />
      <button
        class="bt-back-1 bt-nav-1 ripple fs-md py-2 my-2 fw-bold"
        @click="sendEmail"
      >
        發送
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      connectInfo: [
        { text: "暫不提供", icon: "phoneon" },
        { text: "暫不提供", icon: "font-publish--" },
        { text: "暫不提供", icon: "Fax" },
        { text: "a098400926@gmail.com", icon: "email" },
      ],
      comment: {
        title: "Comment",
        commentList: [
          { place: "你的姓名", text: "" },
          { place: "E-mail", text: "" },
          { place: "主題", text: "" },
          { place: "留言內容", text: "" },
        ],
      },
    };
  },
  methods: {
    sendEmail() {
      let to = "a0984009426@gmail.com";
      let name = this.comment.commentList[0].text;
      let email = this.comment.commentList[1].text;
      let subject = this.comment.commentList[2].text;
      let content = this.comment.commentList[3].text;
      
      let body = "" + content + "%0A%0A%0A";
      body += "From：" + name + "%0A";
      body += "Email：" + email + "%0A";
      
      window.location.href =
        "mailto:" + to + "?subject=" + subject + "&body=" + body;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables.scss";
.footer-contact {
  .send-comment {
    // 按鈕發送
    button {
      width: 25rem;
      height: auto;
    }
    // 輸入框
    textarea {
      width: 25rem;
      height: 2.4rem; // 設置高度會比較好看 不然他會加入卷軸高度
      line-height: 1.8rem; // 讓placeholder保持在中間
      border: 1px solid map-get($colors, "white");
      text-align: top; // 讓光標或是Placeholder保持在前面
      overflow: hidden; // 不顯示捲軸
      resize: none; //不讓使用者更換大小
      transition: all 0.3s ease;
      //   最後一個輸入框
      &:nth-child(5) {
        height: 8rem;
        padding-bottom: 6rem;
      }
      // 提示文字
      &::placeholder {
        font-size: 1rem;
        color: map-get($colors, "white");
        opacity: 0.5;
        text-align: top;
      }
      // 點擊輸入時
      &:focus {
        border: 1px solid map-get($colors, "primary");
        &::placeholder {
          transform: translateX(15px);
          opacity: 0;
          transition: all 0.3s ease;
        }
      }
    }
  }
}

// 布局改垂直 高度增加
@media all and (max-width: 900px) {
  .footer-contact {
    flex-direction: column;
    .my-connect {
      margin: 0 7.5rem 2rem 0;
    }
    .send-comment {
      margin: 0;
    }
  }
}
</style>