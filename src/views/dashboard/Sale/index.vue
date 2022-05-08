<template>
  <div>
    <el-card class="box-card" style="margin: 10px 0">
      <div slot="header" class="clearfix">
        <!-- 头部左侧内容 -->
        <el-tabs class="tab" v-model="activeName">
          <el-tab-pane label="销售额" name="sale"> </el-tab-pane>
          <el-tab-pane label="访问量" name="visite"> </el-tab-pane>
        </el-tabs>
        <!-- 头部右侧内容 -->
        <div class="right">
          <span @click="setDay">今日</span>
          <span @click="setWeek">本周</span>
          <span @click="setMonth">本月</span>
          <span @click="setYear">本年</span>
          <!-- 日期 -->
          <el-date-picker
            type="daterange"
            range-separator="-"
            start-placeholder="开始日期"
            end-placeholder="结束日期"
            size="mini"
            class="date"
            v-model="date"
            value-format="yyyy-MM-dd"
          >
          </el-date-picker>
        </div>
      </div>
      <div>
        <el-row :gutter="10">
          <el-col :span="17">
            <!-- 容器 -->
            <div class="charts" ref="charts"></div>
          </el-col>
          <el-col :span="7">
            <!-- 门店销售额排名 -->
            <div>
              <h5>门店{{ title }}排名</h5>
              <ul>
                <li>
                  <span class="lIndex">1</span>
                  <span>肯德基</span>
                  <span class="rValue">333.234</span>
                </li>
                <li>
                  <span class="lIndex">2</span>
                  <span>麦当劳</span>
                  <span class="rValue">299.132</span>
                </li>
                <li>
                  <span class="lIndex">3</span>
                  <span>肯德基</span>
                  <span class="rValue">289.998</span>
                </li>
                <li>
                  <span style="margin-left: 6px; padding-right: 5px">4</span>
                  <span>海底捞</span>
                  <span class="rValue">266.233</span>
                </li>
                <li>
                  <span style="margin-left: 6px; padding-right: 5px">5</span>
                  <span>手擀面</span>
                  <span class="rValue">223.445</span>
                </li>
                <li>
                  <span style="margin-left: 6px; padding-right: 5px">6</span>
                  <span>汉堡王</span>
                  <span class="rValue">219.663</span>
                </li>
                <li>
                  <span style="margin-left: 6px; padding-right: 5px">7</span>
                  <span>蒸功夫</span>
                  <span class="rValue">200.997</span>
                </li>
              </ul>
            </div>
          </el-col>
        </el-row>
      </div>
    </el-card>
  </div>
</template>

<script>
// 引入echarts
import * as echarts from 'echarts'
// 引入dayjs
import dayjs from 'dayjs'
import { mapState } from 'vuex'
export default {
  name: 'Sale',
  data() {
    return {
      activeName: 'sale',
      mycharts: null,
      // 收集日历数据
      date: []
    }
  },
  mounted() {
    // 初始化echarts实例
    this.mycharts = echarts.init(this.$refs.charts)
    // 配置数据
    this.mycharts.setOption({
      title: {
        text: this.title + '趋势'
      },
      tooltip: {
        trigger: 'axis',
        axisPointer: {
          type: 'shadow'
        }
      },
      grid: {
        left: '3%',
        right: '4%',
        bottom: '3%',
        containLabel: true
      },
      xAxis: [
        {
          type: 'category',
          data: ['一月', '二月', '三月', '四月', '五月', '六月', '七月', '八月', '九月', '十月', '十一月', '十二月'],
          axisTick: {
            alignWithLabel: true
          }
        }
      ],
      yAxis: [
        {
          type: 'value'
        }
      ],
      series: [
        {
          name: 'Direct',
          type: 'bar',
          barWidth: '60%',
          data: [10, 45, 120, 34, 380, 320, 20, 35, 402, 193, 420, 341]
        }
      ]
    })
  },
  computed: {
    // 计算属性-标题
    title() {
      return this.activeName == 'sale' ? '销售额' : '访问量'
    },
    attr() {
      return this.activeName == 'sale'
        ? [10, 45, 120, 34, 380, 320, 20, 35, 402, 193, 420, 341]
        : [105, 450, 110, 304, 30, 20, 200, 350, 202, 19, 40, 54]
    }
  },
  // 监听属性
  watch: {
    title() {
      // 重新修改图标的配置数据
      this.mycharts.setOption({
        title: {
          text: this.title + '趋势'
        },
        series: [
          {
            name: 'Direct',
            type: 'bar',
            barWidth: '60%',
            data: this.attr
          }
        ]
      })
    }
  },
  methods: {
    // 本天
    setDay() {
      const day = dayjs().format('YYYY-MM-DD')
      this.date = [day, day]
    },
    // 本周
    setWeek() {
      const start = dayjs().day(1).format('YYYY-MM-DD')
      const end = dayjs().day(7).format('YYYY-MM-DD')
      this.date = [start, end]
    },
    // 本月
    setMonth() {
      const start = dayjs().startOf('month').format('YYYY-MM-DD')
      const end = dayjs().endOf('month').format('YYYY-MM-DD')
      this.date = [start, end]
    },
    // 本年
    setYear() {
      const start = dayjs().startOf('year').format('YYYY-MM-DD')
      const end = dayjs().endOf('year').format('YYYY-MM-DD')
      this.date = [start, end]
    }
  }
}
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  list-style: none;
}
.clearfix {
  position: relative;
  display: flex;
  justify-content: space-between;
}
.tab {
  width: 100%;
}
.right {
  position: absolute;
  right: 0;
}
.date {
  width: 250px !important;
  margin: 0 20px;
}
.right span {
  margin: 0 10px;
}
.charts {
  width: 100%;
  height: 300px;
}
ul {
  padding-top: 15px;
  width: 100%;
  height: 300px;
}
ul li {
  margin-left: 8px;
  height: 40px;
}
ul li span {
  margin-right: 20px;
}
.lIndex {
  float: left;
  text-align: center;
  width: 17px;
  height: 17px;
  border-radius: 50%;
  background-color: #000;
  color: #fff;
}
.rValue {
  float: right;
}
</style>
