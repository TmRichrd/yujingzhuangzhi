<template>
  <div class="app-container">
    <el-card>
      <div slot="header" class="clearfix">
        <span>路段列表</span>
      </div>
      <avue-crud :option="option" :data="data" :page.sync="page" @on-load="onLoad">
        <template slot="zhuangzhiForm">
          <avue-crud :option="zzoption" :data="zzdata" :page.sync="zzpage">
            <template slot-scope="{row}" slot="menu">
              <el-button type="text" size="small" icon="el-icon-edit" @click="dialogVisible = false">编辑</el-button>
            </template>
          </avue-crud>
        </template>
      </avue-crud>
    </el-card>
    <el-dialog title="绑定/解绑预警装置" :visible.sync="dialogVisible" width="60%">
      <avue-crud :option="zzoption" :data="zzdata" :page.sync="zzpage">
        <template slot-scope="{row}" slot="menu">
          <el-button type="text" size="small" icon="el-icon-edit" @click="dialogVisible = false">编辑</el-button>
        </template>
      </avue-crud>
      <span slot="footer" class="dialog-footer">
        <el-button type="primary" icon="el-icon-circle-plus-outline" @click="dialogVisible = false">绑 定</el-button>
        <el-button icon="el-icon-circle-close" @click="dialogVisible = false">解 绑</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>
export default {
  data () {
    return {
      zzdata: [
        {
          ID: "1"
        },
        {
          id: "2"
        },
      ],
      zzpage: {
        pageSize: 20,
        total: 0
      },
      zzoption: {
        border: false,
        size: "medium",
        index: true,
        headerAlign: 'center',
        align: 'center',
        addBtn: false,
        searchIndex: 3,
        searchIcon: true,
        editBtn: false,
        selection: true,
        header: false,
        delBtn: false,
        column: [
          {
            width: 130,
            label: 'ID',
            prop: 'id',
          },
          {
            label: '编号',
            prop: 'sex',
          },
          {
            label: '状态',
            prop: 'status',
            type: "select",
            dicData: [
              {
                label: "在线",
                value: 1
              },
              {
                label: "离线",
                value: 0
              }
            ]
          },
          {
            label: '电量',
            prop: 'sex',
          },
          {
            label: "装置门"
          },
          {
            label: "运营商"
          },
          {
            label: "创建日期"
          }
        ]
      },
      dialogVisible: false,
      page: {
        pageSize: 20,
        total: 0
      },
      option: {
        border: false,
        size: "medium",
        index: true,
        headerAlign: 'center',
        align: 'center',
        // dialogWidth: "40%",
        searchIndex: 3,
        searchIcon: true,
        editBtn: true,
        column: [
          {
            width: 130,
            label: 'ID',
            prop: 'id',
            display: false
          },
          {
            label: '路段名',
            prop: 'sex',
            span: 24,
            // offset: 2,
            rules: [
              {
                required: true,
                message: "请输入路段名",
                trigger: "blur"
              }
            ]
          },
          {
            label: '路段描述',
            prop: 'sex',
            type: "textarea",
            span: 24,
            // offset: 2,
            rules: [
              {
                required: true,
                message: "请输入路段描述",
                trigger: "blur"
              }
            ]
          },
          {
            label: '预警装置',
            prop: 'zhuangzhi',
            readonly: true,
            placeholder: "请选择预警装置",
            formSlot: true,
            span: 24,
            // offset: 2,
            rules: [
              {
                required: true,
                message: "请选择预警装置",
                trigger: "blur"
              }
            ]
          },
          {
            label: "创建日期",
            display: false,
          }
        ]
      },
      data: [
        {
          ID: "1"
        }
      ],
    }
  },
  methods: {
    handleView () {
      this.$router.push('roadDetail')
    },
    handleShowTable () {
      console.log('====================================');
      console.log(1);
      console.log('====================================');
      this.dialogVisible = true
    },
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

<style lang="scss" scoped></style>