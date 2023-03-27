<template>
  <div class="app-container">
    <avue-crud :option="option" :data="data" :page.sync="page" @on-load="onLoad">
      <template slot-scope="{row,index}" slot="menu">
        <el-button type="text" icon="el-icon-lock" size="small">权限设置</el-button>
      </template>
    </avue-crud>
  </div>
</template>

<script>
export default {
  data () {
    return {
      page: {
        pageSize: 20
      },
      data: [
        {
          id: 5,
          name: "test1",
          remark: "ads1",
          status: 1
        }
      ],
      option: {
        border: true,
        index: true,
        filterBtn:false,
        headerAlign: 'center',
        align: 'center',
        dialogWidth: "40%",
        column: [{
          label: 'ID',
          prop: 'id',
          display: false,
        },
        {
          label: '角色名称',
          prop: 'name',
          rules: [{
            required: true,
            message: "请输入角色名称",
            trigger: "blur"
          }],
          span: 12,
          offset: 4
        },
        {
          label: '角色描述',
          prop: 'remark',
          rules: [{
            required: true,
            message: "请输入角色描述",
            trigger: "blur"
          }],
          span: 12,
          offset: 4
        },
        {
          label: '状态',
          prop: 'status',
          type: "radio",
          span: 12,
          offset: 4,
          value: 1,
          dicData: [
            {
              label: "启用",
              value: 1
            },
            {
              label: "禁用",
              value: 0
            }
          ]
        },
        ]
      },
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: ''
      }
    }
  },
  methods: {
    onLoad (page) {
      //模拟分页
      this.page.total = 40
    },
    onSubmit () {
      this.$message('submit!')
    },
    onCancel () {
      this.$message({
        message: 'cancel!',
        type: 'warning'
      })
    }
  }
}
</script>

<style scoped>
.line {
  text-align: center;
}
</style>

