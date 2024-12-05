<template>
  <div id="app">
    <h1>Vue + Element Plus + ECharts</h1>
    <el-button type="primary">Element Plus Button</el-button>
    <el-input v-model="inputValue" placeholder="Enter text"></el-input>
    
    <div ref="echartsContainer" style="height: 400px;"></div>
  </div>
</template>

<script>
import * as echarts from 'echarts';

export default {
  data() {
    return {
      inputValue: '',
    };
  },
  mounted() {
    const chartContainer = this.$refs.echartsContainer;
    const chart = echarts.init(chartContainer);

    const options = {
      title: {
        text: 'ECharts Example',
      },
      tooltip: {},
      xAxis: {
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
      },
      yAxis: {},
      series: [
        {
          name: 'Sales',
          type: 'bar',
          data: [10, 22, 43, 36, 20, 14, 32],
        },
      ],
    };

    chart.setOption(options);
  },
};
</script>

<style scoped>
/* 可以在这里添加本地样式 */
</style>
