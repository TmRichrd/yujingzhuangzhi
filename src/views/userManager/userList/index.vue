<template>
  <div class="app-container">
    <el-card>
      <div slot="header" class="clearfix">
        <span>用户列表</span>
      </div>
      <avue-crud :option="option" :data="data" :page.sync="page" @on-load="onLoad">
      </avue-crud>
    </el-card>
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
        border: false,
        index: true,
        size: 'medium',
        filterBtn: false,
        headerAlign: 'center',
        align: 'center',
        dialogWidth: "40%",
        labelWidth: 140,
        column: [{
          label: 'ID',
          prop: 'id',
          display: false,
        },
        {
          label: '用户名',
          prop: 'name',
          search:true,
          rules: [{
            required: true,
            message: "请输入用户名",
            trigger: "blur"
          }],
          span: 12,
          offset: 2
        },
        {
          label: '密码',
          prop: 'password',
          type: "password",
          hide: true,
          rules: [{
            required: true,
            message: "请输入密码",
            trigger: "blur"
          }],
          span: 12,
          offset: 2
        },
        {
          label: '最后登录IP',
          prop: 'remark',
          span: 12,
          offset: 2,
          display: false,
        },
        {
          label: '最后登录时间',
          prop: 'status',
          span: 12,
          display: false,
          offset: 2,
        },
        {
          label: '邮箱',
          prop: 'email',
          search:true,
          hide: false,
          rules: [{
            required: true,
            message: "请输入邮箱",
            trigger: "blur"
          }],
          span: 12,
          offset: 2,
        },
        {
          label: '公司名称',
          prop: 'email',
          span: 12,
          offset: 2,
          hide: true
        },
        {
          label: '用户所属设备组',
          type: "select",
          prop: 'email',
          rules: [{
            required: true,
            message: "请选择用户所属设备组",
            trigger: "change"
          }],
          span: 12,
          offset: 2,
          hide: true
        },
        {
          label: '角色',
          type: "select",
          prop: 'email',
          rules: [{
            required: true,
            message: "请选择角色",
            trigger: "change"
          }],
          dicData:[
            {
              label:"1",
              value:"1"
            }
          ],
          span: 12,
          offset: 2,
          hide: true
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

