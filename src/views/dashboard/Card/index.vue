<template>
  <div>
    <el-row :gutter="10">
      <el-col :span="6">
        <el-card>
          <!-- 第一个card -->
          <Detail title="总销售额" count="￥ 126560">
            <template slot="charts">
              <span
                >周同比&nbsp;&nbsp;56.67%
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
                  <path
                    d="M512 405.333333L298.666667 618.666667h426.666666L512 405.333333z"
                    fill="red"
                    p-id="2268"
                  ></path></svg
              ></span>
              <span
                >日同比&nbsp;&nbsp;19.96%
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
                  <path
                    d="M512 618.666667L298.666667 405.333333h426.666666L512 618.666667z"
                    fill="#1afa29"
                    p-id="3247"
                  ></path></svg
              ></span>
            </template>
            <template slot="footer">
              <span>日销售额￥ 123123</span>
            </template>
          </Detail>
        </el-card>
      </el-col>
      <el-col :span="6"
        ><el-card>
          <!-- 第二个card -->
          <Detail title="访问量" count="88460">
            <template slot="charts">
              <LineChart></LineChart>
            </template>
            <template slot="footer">
              <span>日访问量 123123</span>
            </template>
          </Detail>
        </el-card></el-col
      >
      <el-col :span="6"
        ><el-card>
          <!-- 第三个card -->
          <Detail title="支付笔数" count="120120">
            <template slot="charts">
              <BarChart></BarChart>
            </template>
            <template slot="footer">
              <span>转化率65%</span>
            </template></Detail
          >
        </el-card></el-col
      >
      <el-col :span="6"
        ><el-card>
          <!-- 第四个card -->
          <Detail title="运营活动效果" count="78%">
            <template slot="charts">
              <ProgressChart></ProgressChart>
            </template>
            <template slot="footer">
              <span
                >周同比&nbsp;&nbsp;12%
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
                  <path
                    d="M512 405.333333L298.666667 618.666667h426.666666L512 405.333333z"
                    fill="red"
                    p-id="2268"
                  ></path></svg
              ></span>
              <span
                >日同比&nbsp;&nbsp;11%
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
                  <path
                    d="M512 618.666667L298.666667 405.333333h426.666666L512 618.666667z"
                    fill="#1afa29"
                    p-id="3247"
                  ></path></svg
              ></span> </template
          ></Detail> </el-card
      ></el-col>
    </el-row>
  </div>
</template>

<script>
import Detail from './Detail'
import LineChart from './lineChart'
import BarChart from './barCharts'
import ProgressChart from './progressCharts'
export default {
  name: 'card',
  components: {
    Detail,
    LineChart,
    BarChart,
    ProgressChart
  }
}
</script>

<style></style>
