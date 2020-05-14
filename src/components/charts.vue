<template>
  <div id="app">
    <div :id="id"
         style="width:100%; height:500px;"
         ref="Echart"></div>
  </div>
</template>
<script>
import echarts from "echarts";
export default {
  name: "App",
  data: function () {
    return {
      id: this.generatorOnlyId(),
      option: {
        title: {

        },
        tooltip: {
        },
        legend: {
        },
        toolbox: {
        },
        grid: {

        },
        xAxis: [

        ],
        yAxis: [

        ],
        series: [

        ]
      }
    };

  },
  props: ["title", "tooltip", 'legend', 'toolbox', 'grid', 'xAxis', 'yAxis', 'series', "activeName"],
  methods: {

    generatorOnlyId () {
      return (
        this.$moment().format("YYYYMMDDHHmmssSSS") +
        Math.floor(Math.random() * 10000)
      );
    },
    drawChart () {
      // 基于准备好的dom，初始化echarts实例
      let myChart = echarts.init(document.getElementById(this.id));

      // 

      if (this.title !== 'undefind') {
        this.option.title = this.title
      }
      if (this.tooltip !== 'undefind') {
        this.option.tooltip = this.tooltip
      }
      if (this.legend !== 'undefind') {
        this.option.legend = this.legend
      }
      if (this.toolbox !== 'undefind') {
        this.option.toolbox = this.toolbox
      }
      if (this.grid !== 'undefind') {
        this.option.grid = this.grid
      }
      if (this.xAxis !== 'undefind') {
        this.option.xAxis = this.xAxis
      }
      if (this.yAxis !== 'undefind') {
        this.option.yAxis = this.yAxis
      }
      if (this.series !== 'undefind') {
        this.option.series = this.series
      }

      // this.id = Date.parse(new Date());
      // 使用刚指定的配置项和数据显示图表。
      this.$nextTick(() => {
        myChart.resize()

      })
      myChart.setOption(this.option);
    }
  },
  watch: {
    drawChart: function (newVal, oldVal) {
      console.log(newVal)
      console.log(oldVal)

    },
    //正确给 cData 赋值的 方法
    title: function (newVal, oldVal) {

      this.option.title = newVal;  //newVal即是chartData
      console.log(newVal)
      console.log(oldVal)

    },
    tooltip: function (newVal, oldVal) {
      this.option.tooltip = newVal;  //newVal即是chartData

    },
    legend: function (newVal, oldVal) {
      this.option.legend = newVal;  //newVal即是chartData

    },
    toolbox: function (newVal, oldVal) {
      this.option.toolbox = newVal;  //newVal即是chartData

    },
    grid: function (newVal, oldVal) {
      this.option.grid = newVal;  //newVal即是chartData

    },
    xAxis: function (newVal, oldVal) {
      this.option.xAxis = newVal;  //newVal即是chartData

    },
    yAxis: function (newVal, oldVal) {
      this.option.yAxis = newVal;  //newVal即是chartData

    },
    series: function (newVal, oldVal) {
      this.option.series = newVal;  //newVal即是chartData

    },
    activeName: function (newVal, oldVal) {
      console.log(newVal)
      this.drawChart();
      //newVal即是chartData

    },
  },
  mounted () {
    // echarts.init(document.getElementById('report'))
    this.drawChart();
    // console.log(this.props.title)

  },
  // updated () {
  //   console.log(this.activeName)
  //   this.selfAdaption()


  //   // console.log(this.props.title)
  // }
};
</script>
<style>
.my-chart {
  width: 800px;
  height: 500px;
}
</style>
