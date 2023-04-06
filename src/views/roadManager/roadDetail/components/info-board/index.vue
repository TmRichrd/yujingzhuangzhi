<template>
  <div>
    <el-card style="margin-bottom: 20px;">
      <div slot="header" class="clearfix">
        <span>基本信息</span>
      </div>
      <avue-form :option="option" @submit="submit" v-model="form">
      </avue-form>
    </el-card>
    <el-card>
      <div slot="header" class="clearfix">
        <span>运行方案</span>
      </div>
      <avue-form :option="option2">
        <template slot="kongzhi">
          <el-button size="medium" type="primary" block @click="handleSetRule">设置</el-button>
        </template>
      </avue-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {},
      option2: {
        span: 8,
        size: "large",
        labelWidth: 110,
        labelPosition: "top",
        column: [
          {
            type: "select",
            label: "工作模式",
            span: 5,
            offset: 0,
            dicData: [
              {
                label: "模式1",
                value: 1
              }
            ]
          },
          {
            label: "亮度选择",
            type: "select",
            span: 5,
            offset: 4,
            dicData: [
              {
                label: "模式1",
                value: 1
              }
            ]
          },
          {
            label: "规则控制",
            prop: "kongzhi",
            span: 5,
            offset: 4,
          }
        ]
      },
      option: {
        span: 8,
        size: "large",
        labelWidth: 110,
        labelPosition: "top",
        column: [
          {
            label: '预警装置',
            prop: 'input',
            type: 'select',
            span: 5,
            labelPosition: "right",
            multiple: true,
            dicData: [
              {
                label: "装置1",
                value: 1
              }
            ]
          },
          {
            label: '名称设置',
            prop: 'input1',
            span: 5,
            offset: 4,
          },
          {
            label: '显示文字',
            prop: 'input1',
            span: 5,
            offset: 4,
          },
          {
            label: '文字颜色',
            prop: 'input12',
            type: "color",
            span: 5,
            offset: 0,
          },
          {
            label: '输入安装地点',
            prop: 'input1',
            span: 5,
            offset: 4,
          },
          {
            label: "地图定位",
            prop: "map",
            span: 5,
            offset: 4,
          },
          {
            label: "电量情况",
            span: 5,
            offset: 0,
          },
          {
            label: "在线状态",
            span: 5,
            offset: 4,
          }
        ]
      },
    }
  },
  methods: {
    submit (form, done) {
      console.log('====================================');
      console.log(form);
      console.log('====================================');
      done()
    },
    handleSetRule () {
      this.$router.push('/device/ruleController')
    }
  },
}
</script>

<style lang="scss" scoped></style>