<template>
  <div class="app-container">
    <el-card>
      <div slot="header" class="clearfix">
        <span>规则控制</span>
      </div>
      <avue-crud :option="option" :data="data" :page.sync="page" @on-load="onLoad">
        <!-- <template slot="timeForm">
          <el-row :gutter="8">
            <el-col :span="5">
              <el-select></el-select>
            </el-col>
            <el-col :span="5">
              <el-select></el-select>
            </el-col>
            <el-col :span="2">
              <div style="text-align: center;color: #fff;">
                至
              </div>
            </el-col>
            <el-col :span="5">
              <el-select></el-select>
            </el-col>
            <el-col :span="5">
              <el-select></el-select>
            </el-col>
          </el-row>
        </template> -->
      </avue-crud>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      data: [
        {
          id: 1
        }
      ],
      page: {
        pageSize: 20,
        total: 0
      },
      option: {
        size: "medium",
        border: false,
        index: true,
        filterBtn: false,
        headerAlign: 'center',
        align: 'center',
        dialogWidth: "40%",
        addBtn: false,
        column: [
          {
            label: 'ID',
            prop: "id",
            display: false,
          },
          // {
          //   label: "起止时间",
          //   prop: "time",
          //   formslot: true,
          //   span: 20
          // },
          {
            label:"时长",
            span: 13
          },
          {
            label: "播放文字",
            prop: "mode",
            span: 13
          },
          {
            label: "显示文字",
            prop: "liangdu",
            span: 13
          },
        ]
      }
    }
  },
  methods: {
    onLoad () {

    }
  },
}
</script>

<style lang="scss" scoped></style>