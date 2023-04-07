<template>
  <div class="app-container">
    <el-card>
      <div slot="header" class="clearfix">
        <span>路段列表</span>
      </div>
      <avue-crud :option="option" :data="data" :page.sync="page" @on-load="onLoad">
        <!-- <template slot="menu" slot-scope="{row,index}">
          <el-button @click="handleView" type="text" icon="el-icon-edit" size="small">编辑</el-button>
        </template> -->
      </avue-crud>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      page: {
        pageSize: 20,
        total: 0
      },
      option: {
        border: false,
        size:"medium",
        index: true,
        headerAlign: 'center',
        align: 'center',
        dialogWidth: "40%",
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
            span: 12,
            offset: 2,
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
            span: 12,
            offset: 2,
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
            prop: 'sex',
            type: "select",
            multiple: true,
            span: 12,
            offset: 2,
            rules: [
              {
                required: true,
                message: "请输入路段描述",
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