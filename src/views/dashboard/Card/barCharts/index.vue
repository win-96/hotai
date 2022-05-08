<template>
  <div>
    <!-- 容器 -->
    <div class="charts" ref="charts"></div>
  </div>
</template>

<script>
// 引入 echarts
import * as echarts from 'echarts'
export default {
  name: '',
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
          // 图表的形式
          type: 'bar',
          data: [78, 20, 33, 72, 88, 20, 19, 78, 45, 78, 24, 24],
          color: 'cyan'
        }
      ],
      // 布局调试
      grid: {
        left: 0,
        top: 0,
        right: 0,
        bottom: 0
      },
      // 提示信息
      tooltip: {}
    })
  }
}
</script>

<style scoped>
.charts {
  width: 100%;
  height: 50px;
}
</style>
