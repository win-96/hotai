<template>
  <div>
    <div class="header">
      <span class="search-header">搜索用户数</span>
      <svg
        t="1643014263688"
        class="icon"
        viewBox="0 0 1024 1024"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        p-id="1231"
        width="14"
        height="14"
      >
        <path
          d="M511.999436 0.000376c-282.769574 0-511.999059 229.230238-511.99906 511.999436s229.229486 511.999436 511.99906 511.999435c282.769197 0 511.998683-229.230238 511.998683-511.999435S794.768633 0.000376 511.999436 0.000376z m-0.000753 991.998695c-265.095346 0-479.998507-214.90316-479.998507-479.999259S246.903336 32.000553 511.998683 32.000553c265.096475 0 479.999635 214.90316 479.999635 479.999259s-214.90316 479.999259-479.999635 479.999259z"
          fill=""
          p-id="1232"
        ></path>
        <path
          d="M511.998683 223.999353m-32.000176 0a32.000176 32.000176 0 1 0 64.000352 0 32.000176 32.000176 0 1 0-64.000352 0Z"
          fill=""
          p-id="1233"
        ></path>
        <path
          d="M543.999236 799.999518c0 17.673475-14.327078 31.9998-32.000553 31.9998-17.672722 0-31.9998-14.326325-31.9998-31.9998V351.999683c0-17.673098 14.327078-31.9998 31.9998-31.999801 17.673475 0 32.000553 14.326702 32.000553 31.999801v447.999835z"
          fill=""
          p-id="1234"
        ></path>
      </svg>
    </div>
    <div class="main">
      <span class="main-title">2161541</span>
      <span class="main-content">17.1</span>
      <svg
        t="1643015405087"
        class="icon"
        viewBox="0 0 1024 1024"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        p-id="2267"
        width="16"
        height="16"
      >
        <path d="M512 405.333333L298.666667 618.666667h426.666666L512 405.333333z" fill="red" p-id="2268"></path>
      </svg>
      <svg
        t="1643015575642"
        class="icon"
        viewBox="0 0 1024 1024"
        version="1.1"
        xmlns="http://www.w3.org/2000/svg"
        p-id="3246"
        width="16"
        height="16"
      >
        <path d="M512 618.666667L298.666667 405.333333h426.666666L512 618.666667z" fill="#1afa29" p-id="3247"></path>
      </svg>
    </div>
    <div class="footer">
      <div class="charts" ref="charts"></div>
    </div>
  </div>
</template>

<script>
// 引入 echarts
import * as echarts from 'echarts'
export default {
  name: 'lineCharts',
  mounted() {
    // 初始化echarts实例
    let lineCharts = echarts.init(this.$refs.charts)

    // 配置数据
    lineCharts.setOption({
      xAxis: {
        // 隐藏x轴
        show: false,
        type: 'category'
      },
      yAxis: {
        // 隐藏y轴
        show: false
      },
      // 系列
      series: [
        {
          type: 'line',
          data: [78, 20, 33, 72, 88, 20, 19, 78, 45, 78, 24, 52, 62, 54],
          // 拐点的样式设置
          itemStyle: {
            opacity: 0
          },
          // 线条的样式
          lineStyle: {
            color: 'bule'
          },
          // 填充颜色的样式
          areaStyle: {
            color: {
              type: 'linear',
              x: 0,
              y: 0,
              x2: 0,
              y2: 1,
              colorStops: [
                {
                  offset: 0,
                  color: 'blue' // 0% 处的颜色
                },
                {
                  offset: 1,
                  color: '#fff' // 100% 处的颜色
                }
              ],
              global: false // 缺省为 false
            }
          }
        }
      ],
      // 布局调试
      grid: {
        left: 0,
        top: 0,
        right: 0,
        bottom: 0
      }
    })
  }
}
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
}
.search-header {
  margin-right: 20px;
}
.main {
  margin: 10px 0;
}
.main-title {
  margin-right: 30px;
}
.main-content {
  margin-right: 10px;
}
.charts {
  width: 100%;
  height: 50px;
}
</style>
