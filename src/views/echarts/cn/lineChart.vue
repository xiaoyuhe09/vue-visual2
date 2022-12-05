<template>
  <div ref="myChart" id="lineChart"></div>
</template>

<script>
import * as echarts from "echarts";
export default {
  mounted() {
    let myChart = echarts.init(this.$refs.myChart);
    // let yearlist = ['2022','2023']
    let result = [
      { name: "22年1月", ai: 416649, ai2: 995004 },
      { name: "22年2月", ai: 395992, ai2: 937604 },
      { name: "22年3月", ai: 429375, ai2: 1055528 },
      { name: "22年4月", ai: 437912, ai2: 978920 },
      { name: "22年5月", ai: 441174, ai2: 928960 },
      { name: "22年6月", ai: 391193, ai2: 932307 },
      { name: "22年7月", ai: 551169, ai2: 1253081 },
      { name: "22年8月", ai: 440622, ai2: 931956 },
      { name: "22年9月", ai: 370788, ai2: 800851 },
      { name: "22年10月", ai: 312339, ai2: 68951 },
    ];

    let xData = result.map((item) => {
      return item.name;
    });
    let keys = ["ai", "ai2"],
      seriesData = [];
    let color = ["0, 254, 210", "0, 124, 250"];
    keys.forEach((key, index) => {
      seriesData.push({
        name: key + "数",
        data: result.map((item) => {
          return item[key];
        }),
        type: "line",
        yAxisIndex: 0,
        symbol: "none",
        symbolSize: 7,
        barWidth: 14,
        splitNumber: 6,
        smooth: false,
        itemStyle: {
          color: `rgba(${color[index]},1)`,
        },
        lineStyle: {
          color: `rgba(${color[index]},1)`,
          width: 1,
        },
        areaStyle: {
          opacity: 1,
          color: {
            x: 0,
            y: 0,
            x2: 0,
            y2: 1,
            type: "linear",
            global: false,
            colorStops: [
              {
                offset: 0,
                color: `rgba(${color[index]},0.35)`,
              },
              {
                offset: 0.8,
                color: "rgba(6, 8, 41,.1)",
              },
            ],
          },
          shadowColor: "rgba(0, 0, 0, 0.1)",
          shadowBlur: 10,
        },
      });
      seriesData.push({
        name: key + "数",
        data: [
          {
            coords: result.map((item) => {
              return [item.name, item[key]];
            }),
          },
        ],
        type: "lines",
        coordinateSystem: "cartesian2d",
        zlevel: 1,
        polyline: true,
        smooth: true,
        symbol: "circle",
        effect: {
          show: true,
          trailLength: 0.4,
          symbol: "circle",
          period: 8,
          symbolSize: 8,
        },
        lineStyle: {
          normal: {
            color: `rgba(${color[index]},1)`,
            width: 0,
            opacity: 0,
            curveness: 0,
          },
        },
      });
    });

    let option = {
      // backgroundColor: "#1b1b1b",
      tooltip: {
        trigger: "axis",
        axisPointer: {
          type: "line",
        },
        padding: [8, 15],
        backgroundColor: "rgba(12, 51, 115,0.8)",
        borderColor: "rgba(3, 11, 44, 0.5)",
        textStyle: {
          color: "rgba(255, 255, 255, 1)",
        },
      },
      grid: {
        show: true,
        top: 50,
        left: 20,
        right: 30,
        bottom: 36,
        containLabel: true,
        borderWidth: 0,
        backgroundColor: "rgba(12, 45, 81, .3)",
      },
      legend: {
        show: true,
        top: 0,
        right: 30,
        itemWidth: 14,
        itemHeight: 2,
        itemGap: 24,
        icon: "react",
        textStyle: {
          padding: [0, 0, 0, 4],
          fontSize: 15,
          color: "#AEC6DF",
        },
      },
      dataZoom: [
        {
          show: true,
          start: 0,
          end: 100,
          bottom: 10,
          right: 8,
          left: 30,
          height: 20,
          borderColor: "transparent",
          showDetail: false,
          backgroundColor: "transparent",
          handleStyle: {
            color: "rgba(64, 169, 255, 0.57)",
          },
          moveHandleSize: 0,
          moveHandleStyle: {
            opacity: 0,
          },
          dataBackground: {
            areaStyle: {
              color: "rgba(64, 169, 255, 1)",
            },
          },
        },
        {
          type: "inside",
          dataBackground: "#0ffs",
          showDetail: false,
        },
      ],
      xAxis: {
        type: "category",
        boundaryGap: false,
        data: xData,
        axisPointer: {
          handle: {
            show: false,
          },
        },
        axisLine: {
          show: false,
          lineStyle: {
            color: "#AEC6DF",
          },
        },
        axisTick: {
          show: false,
        },
      },
      yAxis: [
        {
          show: true,
          nameGap: 0,
          type: "value",
          minInterval: 1,
          splitLine: {
            show: false,
          },
          axisTick: {
            show: false,
          },
          minorSplitLine: {
            show: false,
          },
          axisLine: {
            show: false,
          },
          nameTextStyle: {
            fontSize: 14,
            padding: [0, 0, 0, -15],
            align: "left",
            color: "#AEC6DF;",
          },
          axisLabel: {
            color: "#AEC6DF",
          },
        },
      ],
      series: seriesData,
    };
    myChart.setOption(option);
  },
};
</script>

<style>
#lineChart {
  width: 350px;
  height: 300px;
  margin: 0px auto;
  padding: 30px;
  margin-right: 30px;
  /* background-color: pink; */
}
</style>