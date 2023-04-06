<template>
  <div>
    <el-card>
      <div slot="header" class="clearfix">
        <span>工作参数</span>
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
            label: '工作模式',
            prop: 'input',
            type: 'select',
            value: 1,
            labelPosition: "right",
            dicData: [
              {
                label: "模式1",
                value: 1
              }
            ]
          },
          {
            type: "select",
            label: "播放模式",
            dicData: [
              {
                label: "模式1",
                value: 1
              }
            ]
          },
          {
            label: "规则控制",
            type: "select",
            dicData: [
              {
                label: "模式1",
                value: 1
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