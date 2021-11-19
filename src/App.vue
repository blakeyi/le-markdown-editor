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
        "```mermaid\n" +
        "graph TD\n" +
        "A[runDocker <- dockerCli] -->| 实例化 | B(cmd.Execute )\n" +
        "B -->|执行 | C(c.Traverse)\n" +
        "C -->| 遍历命令| D(c.findNext)\n" +
        "D -->| 预定义了一组Commands,包含所有的docker命令 通过cmd.Name == next过滤命令| F(cmd.execute <- flags)\n" +
        "F -->| 实现接口赋值实现绑定| G(c.RunE <- runImages)\n" +
        "G -->|执行 | H(dockerCli.Client.ImageList)\n" +
        "H -->|获取客户端实例,调用ImageList方法与服务器通信 | I(dockerCli.Client.ImageList)\n" +
        "I -->|GET接口获取数据 | J(cli.get <- /images/json)\n" +
        "J -->|格式化输出 | K(formatter.ImageWrite)\n" +
        "```\n" +
        "```mermaid\n" +
        "graph TD\n" +
        "A[runDocker <- dockerCli] -->| 实例化 | B(cmd.Execute )\n" +
        "B -->|执行 | C(c.Traverse)\n" +
        "C -->| 遍历命令| D(c.findNext)\n" +
        "D -->| 预定义了一组Commands,包含所有的docker命令 通过cmd.Name == next过滤命令| F(cmd.execute <- flags)\n" +
        "F -->| 实现接口赋值实现绑定| G(c.RunE <- runImages)\n" +
        "G -->|执行 | H(dockerCli.Client.ImageList)\n" +
        "H -->|获取客户端实例,调用ImageList方法与服务器通信 | I(dockerCli.Client.ImageList)\n" +
        "I -->|GET接口获取数据 | J(cli.get <- /images/json)\n" +
        "J -->|格式化输出 | K(formatter.ImageWrite)\n" +
        "```",
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
