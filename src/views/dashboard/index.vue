<template>
  <div class="dashboard-container">
    <div style="margin-bottom: 20px;">
      <el-card>
        <avue-data-icons :option="option"></avue-data-icons>
      </el-card>
    </div>
    <baidu-map :scroll-wheel-zoom="true" class="bm-view" @ready="mapReady" :center="center" :zoom="zoom">
    </baidu-map>
    <el-row :gutter="24" style="margin-bottom: 20px;">
      <el-col :span="12">
        <el-card>
          <div id="charts1" style="width: 100%;height:400px;" class="pie-pic" />
        </el-card>
      </el-col>
      <el-col :span="12">
        <el-card>
          <div id="charts2" style="width: 100%;height:400px;" class="pie-pic" />
        </el-card>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="24">
        <el-card>
          <div id="charts3" style="width: 100%;height:400px;" class="pie-pic" />
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import echarts from 'echarts'

export default {
  name: 'Dashboard',
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  data () {
    return {
      center: { lng: 116.404, lat: 39.915 },
      zoom: 15,
      title: 123,
      pieData: {
        luduantotal: 10,
        luduan: 2
      },
      myChart: null,
      option: {
        span: 4,
        data: [
          {
            title: '雷达',
            count: 12678,
            decimals: 2,
            icon: 'el-icon-s-tools',
          },
          {
            title: '预警装置',
            count: 22139,
            icon: 'el-icon-s-help',
          },
          {
            title: '在线',
            count: 35623,
            icon: 'el-icon-success',
          },
          {
            title: '离线',
            count: 16826,
            icon: 'el-icon-error',
          },
          {
            title: '报警',
            count: 16826,
            icon: 'el-icon-message-solid',
          },
          {
            title: '电量不足',
            count: 16826,
            icon: 'el-icon-warning',
          }
        ]
      },
      echartsoOption: {
        title: {
          text: 'Traffic Sources',
          left: 'center',
          textStyle: {
            color: "#fff"
          }
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b} : {c} ({d}%)',
        },
        legend: {
          orient: 'vertical',
          left: 'left',
          data: ['Direct', 'Email', 'Ad Networks', 'Video Ads', 'Search Engines'],
        },
        series: [
          {
            name: 'Traffic Sources',
            type: 'pie',
            radius: '55%',
            center: ['50%', '60%'],
            data: [
              { value: 335, name: 'Direct' },
              { value: 310, name: 'Email' },
              { value: 234, name: 'Ad Networks' },
              { value: 135, name: 'Video Ads' },
              { value: 1548, name: 'Search Engines' },
            ],
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)',
              },
            },
          },
        ],
      }
    }
  },
  mounted () {
    this.lng = 116.404
    this.lat = 39.915
    this.zoom = 15
    var myChart = echarts.init(document.getElementById('charts1'));
    var myChart2 = echarts.init(document.getElementById('charts2'));
    var myChart3 = echarts.init(document.getElementById('charts3'));

    // 指定图表的配置项和数据
    var option = {
      title: {
        text: '雷达数据',
        textStyle: {
          color: "#fff"
        }
      },
      tooltip: {},
      legend: {
        data: ['米']
      },
      xAxis: {
        data: ["3/9", "3/10", "3/11", "3/12", "3/13", "3/14"],
        axisLine: {
          lineStyle: {
            color: "#fff"
          }
        }
      },
      yAxis: {
        axisLine: {
          lineStyle: {
            color: "#fff"
          }
        }
      },
      series: [{
        name: '米',
        type: 'bar',
        data: [5, 20, 36, 10, 10, 20]
      }]
    };
    var option2 = {
      title: {
        text: 'Referer of a Website',
        subtext: 'Fake Data',
        left: 'center',
        textStyle: {
          color: "#fff"
        }
      },
      tooltip: {
        trigger: 'item'
      },
      legend: {
        orient: 'vertical',
        left: 'left',
        itemStyle: {
          color: "#fff"
        },
        lineStyle: {
          color: "#fff"
        },
        textStyle: {
          color: "#fff"
        }

      },
      series: [
        {
          name: 'Access From',
          type: 'pie',
          radius: '50%',
          data: [
            { value: 1048, name: 'Search Engine' },
            { value: 735, name: 'Direct' },
            { value: 580, name: 'Email' },
            { value: 484, name: 'Union Ads' },
            { value: 300, name: 'Video Ads' }
          ],
          emphasis: {
            itemStyle: {
              shadowBlur: 10,
              shadowOffsetX: 0,
              shadowColor: 'rgba(0, 0, 0, 0.5)'
            }
          }
        }
      ]
    };
    var option3 = {
      xAxis: {
        type: 'category',
        boundaryGap: false,
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
        axisLine: {
          lineStyle: {
            color: "#fff"
          }
        }
      },
      yAxis: {
        type: 'value',
        axisLine: {
          lineStyle: {
            color: "#fff"
          }
        }
      },
      series: [
        {
          data: [820, 932, 901, 934, 1290, 1330, 1320],
          type: 'line',
          smooth: true,
          areaStyle: {}
        }
      ]
    }

    // 使用刚指定的配置项和数据显示图表。
    myChart.setOption(option);
    myChart2.setOption(option2);
    myChart3.setOption(option3);
    // this.createChart()
    // window.addEventListener('resize', this.reDraw)
  },
  methods: {
    mapReady ({ BMap, map }) { // 地图初始化完成-添加自定义样式
      // map.setMapStyle({
      //   styleJson: BMapJson
      // })
      map.setMapStyleV2({ styleId: 'b2a5cf3f2709221ab9a68e0872eec809' })
    },
    reDraw () {
      if (this.myChart)
      {
        this.myChart.resize()
      }
    },
    createChart () {
      this.$nextTick(() => {
        this.myChart = echarts.init(document.getElementById('charts1'))
        this.myChart.setOption(this.initOption())
      })
    },
    initOption () {
      const data = {
        xAxis: {
          type: 'category',
          data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
          type: 'value'
        },
        series: [
          {
            data: [150, 230, 224, 218, 135, 147, 260],
            type: 'line'
          }
        ]
      }
      return data
    }
  },
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }

  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}

.chart {
  height: 100vh;
}

#charts1 {
  height: 200px;
}

.bm-view {
  width: 100%;
  height: 443px;
  margin-bottom: 20px;
}
</style>
