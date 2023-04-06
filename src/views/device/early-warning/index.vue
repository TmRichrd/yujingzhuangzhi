<template>
  <div class="app-container">
    <el-card>
      <div slot="header" class="clearfix">
        <span>预警装置</span>
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
        pageSize: 20,
        total: 0
      },
      option: {
        border: false,
        size:"medium",
        index: true,
        headerAlign: 'center',
        align: 'center',
        addBtn: false,
        searchIndex: 3,
        searchIcon: true,
        column: [
          {
            width: 130,
            label: 'ID',
            prop: 'id',
          },
          {
            label: '编号',
            prop: 'sex',
            search: true
          },
          {
            label: '状态',
            prop: 'status',
            search: true,
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
            label:"装置门"
          },
          {
            label: "运营商"
          },
          {
            label: "创建日期"
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