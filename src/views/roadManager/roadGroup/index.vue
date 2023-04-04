<template>
  <div class="app-container">
    <el-card>
      <div slot="header" class="clearfix">
        <span>路段分组</span>
      </div>
      <avue-crud :option="option" ref="crud" :data="data" :page.sync="page" @on-load="onLoad">
        <template slot-scope="scope" slot="menuLeft">
          <el-button type="primary" icon="el-icon-plus" size="small" @click="handleAdd">新增</el-button>
        </template>
      </avue-crud>
    </el-card>
    <el-dialog title="路段分组" :visible.sync="dialogVisible" :before-close="handleClose">
      <el-form label-width="100px">
        <el-row>
          <el-col :span="13" :offset="4">
            <el-form-item label="分组名称:">
              <el-input></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="24">
            <el-form-item>
              <el-transfer :titles="['选择路段', '已添加']" :button-texts="['去除', '添加']" filterable v-model="value"
                :data="generateData"></el-transfer>
            </el-form-item>
          </el-col>
        </el-row>
      </el-form>
      <span slot="footer" class="dialog-footer">
        <el-button size="small" @click="dialogVisible = false">取 消</el-button>
        <el-button size="small" type="primary" @click="dialogVisible = false">确 定</el-button>
      </span>
    </el-dialog>
  </div>
</template>

<script>

export default {
  data () {
    return {
      value: [1, 4],
      dialogVisible: false,
      page: {
        pageSize: 20,
        total: 0
      },
      data: [
        {
          id: 5,
          name: "宁夏高速"
        }
      ],
      option: {
        border: false,
        size:"medium",
        index: true,
        filterBtn: false,
        headerAlign: 'center',
        align: 'center',
        addBtn: false,
        editBtn: false,
        column: [
          {
            label: "编号",
            prop: "id",
            width: 100,
          },
          {
            label: "分组名称",
            prop: "name"
          },
        ]
      },



    }
  },
  computed: {
    generateData () {
      const data = [];
      for (let i = 1; i <= 15; i++)
      {
        data.push({
          key: i,
          label: `备选项 ${i}`,
          disabled: i % 4 === 0
        });
      }
      return data;
    }
  },
  methods: {
    handleAdd () {
      this.dialogVisible = true
    },
    onLoad () {
      this.page.total = 40
    }
  },
}
</script>

<style lang="scss">
.el-transfer-panel,.el-transfer-panel__header{
  text-align: left;
  background: #0A3079 !important;
  color: #fff !important;
}
.el-checkbox__label,.el-checkbox__label span{
  color: #fff !important;
}
.el-transfer-panel{
 border: 1px solid rgba(255, 255, 255, .3)!important;
}
.el-transfer-panel__header{
  border-bottom: 1px solid rgba(255, 255, 255, .3)!important;
}
.el-transfer__button{
  padding: 7px 12px;
}
.el-transfer__button.is-disabled{
  color: #333;
  background: #999;
  border-color: #999;
}
</style>