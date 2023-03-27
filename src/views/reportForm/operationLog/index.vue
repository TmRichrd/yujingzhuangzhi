<template>
  <div class="app-container">
    <avue-crud :option="option" :data="data" :page.sync="page" @on-load="onLoad">
    </avue-crud>
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
        border: true,
        index: true,
        headerAlign: 'center',
        align: 'center',
        dialogWidth: "40%",
        searchIndex: 3,
        excelBtn:true,
        searchIcon: true,
        editBtn: false,
        addBtn: false,
        delBtn:false,
        menu:false,
        column: [
          {
            label: 'ID',
            prop: 'id',
          },
          {
            label: '用户名',
            prop: 'sex',
          },
          {
            label: '操作类型',
            prop: 'action',
          },
          {
            label: "操作内容",
            prop:"content",
          },
          {
            label: "日期",
            prop:"createTime",
            type: "daterange",
            format: "yyyy-MM-dd",
            range: true,
            searchRange:true,
            search: true,
          },
          {
            label: "ip地址",
            prop:"ip",
          },
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