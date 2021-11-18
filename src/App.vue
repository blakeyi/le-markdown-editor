<template>
  <div id="app" :style="appStyle">
    <div id="editor-main">
      <!--      <le-editor v-model="value" :image-uploader="imageUploader" @uploadImg="uploadImg" @save="save"></le-editor>-->
      <le-editor
        v-model="value"
        :indent-unit="4"
        :fullscreen="true"
        :hljs-css="hljsCss"
        :image-uploader="imageUploader"
        @save="save"
      ></le-editor>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      hljsCss: "agate",
      value:
        "# 流程图\n" +
        "```flow\n" +
        "start=>start: 开始\n" +
        "loginInfo=>inputoutput: 登录数据\n" +
        "verifyLogin=>subroutine: 登录验证\n" +
        "isSuccess=>condition: 验证成功？\n" +
        "respondSuccess=>operation: 响应成功\n" +
        "responseFailure=>operation: 响应失败\n" +
        "end=>end: 结束\n" +
        "\n" +
        "start->loginInfo->verifyLogin->isSuccess\n" +
        "isSuccess(yes)->respondSuccess->end\n" +
        "isSuccess(no)->responseFailure->end\n" +
        "```\n",
      appStyle: {
        // width: document.documentElement.clientWidth + 'px',
        // height: document.documentElement.clientHeight + 'px'
      },
      // 自定义
      // imageUploader: {
      //   custom: true,
      //   fileType: 'file',
      //   fileNameType: 'uuid',
      //   imagePrefix: 'https://cdn.jsdelivr.net/gh/', // 图片前缀地址
      // }
      imageUploader: {
        custom: false,
        fileType: "file",
        fileNameType: "",
        imagePrefix: "http://106.54.92.121", // 图片前缀地址
        type: "server",
        url: "http://106.54.92.121:82/upload",
      },
    };
  },
  methods: {
    // 自定义
    // uploadImg: function ($vm, file, fileName) {
    //   console.log($vm)
    //   console.log(file)
    //   console.log(fileName)
    //   // 添加图片
    //   // 两个参数 第一个是图片访问路径 第二个是文件名
    //   $vm.insertImg(`${$vm.config.imageUploader.imagePrefix}${fileName}`, fileName)
    // },
    save: function (val) {
      // 获取预览文本
      console.log(this.value);
      console.log(val);
    },
  },
  mounted() {},
};
</script>

<style lang="scss">
#app {
  width: 100%;
  height: 500px;
  margin: 50px auto;
  display: flex;
  justify-content: center;
}

#editor-main {
  color: #2c3e50;
  width: 85%;
  height: 100%;
}
</style>
