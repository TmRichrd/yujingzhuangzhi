<template>
  <div>
    <el-card>
      <div slot="header" class="clearfix">
        <span>基本信息</span>
      </div>
      <avue-form :option="option" @submit="submit" v-model="form">
      </avue-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      form: {},
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
            labelPosition: "right",
            dicData: [
              {
                label: "装置1",
                value: 1
              }
            ]
          },
          {
            label: '名称设置',
            prop: 'input1'
          },
          {
            label: '输入安装地点',
            prop: 'input1'
          },
          {
            label: "地图定位",
            prop: "map",
          },
          {
            label: "电量情况",
          },
          {
            label: "在线状态"
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
    }
  },
}
</script>

<style lang="scss" scoped></style>