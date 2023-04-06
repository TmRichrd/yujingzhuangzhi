<template>
  <div>
    <el-card>
      <div slot="header" class="clearfix">
        <span>音柱装置</span>
      </div>
      <avue-form :option="option">
      </avue-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      option: {
        span: 8,
        size: "large",
        labelWidth: 110,
        labelPosition: "top",
        column: [
          {
            label: "音柱序列号",
            prop: "id",
            span: 5,
          },

          {
            label: "播报文字",
            prop: "text",
            span: 5,
            offset: 4,
          },
          {
            label: "音量大小",
            type: "slider",
            prop: "value",
            span: 5,
            offset: 4,
          },
          {
            label: "语音声音",
            type: "select",
            prop: "sound",
            span: 5,
            offset: 0,
            dicData: [
              {
                label: "男声",
                value: 1
              },
              {
                label: '女声',
                value: 2
              }
            ]
          },
        ]
      },
    }
  },
}
</script>

<style lang="scss" scoped></style>