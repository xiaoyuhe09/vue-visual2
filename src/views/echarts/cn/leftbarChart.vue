<template>
  <div ref="myChart" id="leftBarChart"></div>
</template>

<script>
import * as echarts from "echarts";
export default {
  mounted() {
    let myChart = echarts.init(this.$refs.myChart);
    let option = {
      // backgroundColor: '#110839',
      grid: {
        left: "20%",
        top: "28%",
        right: "10%",
        bottom: "10%",
      },
      tooltip: {
        trigger: "axis",
        // backgroundColor: "#05050F", // 提示框背景色
        borderColor: "#05050F", // 提示框边框色
        textStyle: {
          color: "#fff", // 提示框文本颜色
        },
        formatter: (params) => {
          debugger;
          // 自定义tooltip小圆点
          const dotHtml1 =
            '<span style="display:inline-block;margin-right:5px;border-radius:10px;width:10px;height:10px;background-color:#FFB166"></span>';
          const dotHtml2 =
            '<span style="display:inline-block;margin-right:5px;border-radius:10px;width:10px;height:10px;background-color:#00FF78"></span>';
          const dotHtml3 =
            '<span style="display:inline-block;margin-right:5px;border-radius:10px;width:10px;height:10px;background-color:#00FFFF"></span>';
          const result = `${dotHtml1} ${params[2].seriesName} : ${
            params[2].value
          }万公顷  &nbsp;&nbsp;|&nbsp;&nbsp;   ${dotHtml2} ${
            params[1].seriesName
          } : ${
            params[1].value / 10
          }%  &nbsp;&nbsp;|&nbsp;&nbsp;   ${dotHtml3} ${
            params[0].seriesName
          } : ${params[0].value}亿元`;
          return result;
        },
        axisPointer: {
          type: "none",
        },
      },
      legend: {
        data: ["项目投入资金(亿元)", "累计造林面积(万公顷)", "森林覆盖率(%)"],
        right: "center",
        top: 10,
        textStyle: {
          //文字样式
          color: "#fff",
          fontSize: "12",
        },
      },
      xAxis: {
        type: "value",
        position: "top",
        splitLine: {
          show: true,
          lineStyle: {
            color: "rgba(98, 162, 205, 0.4)",
          },
        },
        axisTick: {
          show: false,
        },
        axisLabel: {
          textStyle: {
            color: "#fff",
            fontSize: 12,
          },
        },
        axisLine: {
          show: false,
        },
      },
      yAxis: {
        type: "category",
        splitLine: {
          show: false,
        },
        axisTick: {
          show: false,
        },
        data: [
          "三北防护林\n工程",
          "长江中上游\n防护林\n建设工程",
          "沿海防护林\n体系建设\n工程",
          "防沙治沙\n工程",
        ],
        axisLabel: {
          textStyle: {
            color: "#fff",
            fontSize: 12,
          },
        },
        axisLine: {
          lineStyle: {
            color: "rgba(98, 162, 205, 0.4)",
          },
        },
      },
      series: [
        {
          name: "项目投入资金(亿元)",
          type: "bar",
          data: [900, 982, 620, 326],
          itemStyle: {
            emphasis: {
              barBorderRadius: [0, 20, 20, 0],
            },
            normal: {
              barBorderRadius: [0, 20, 20, 0],
              color: new echarts.graphic.LinearGradient(
                0,
                0,
                1,
                0,
                [
                  {
                    offset: 0,
                    color: "rgba(2, 22, 80, 0.2)", // 0% 处的颜色
                  },
                  {
                    offset: 1,
                    color: "rgba(0, 255, 255, 0.8)", // 100% 处的颜色
                  },
                ],
                false
              ),
            },
          },
          label: {
            normal: {
              show: false,
              formatter: "{c}",
              position: "insideRight",
              offset: [-2, 1.5],
              textStyle: {
                color: "#fff",
                fontSize: 10,
              },
            },
          },
        },
        {
          name: "森林覆盖率(%)",
          type: "bar",
          data: [120, 182, 162, 132],
          itemStyle: {
            emphasis: {
              barBorderRadius: [0, 20, 20, 0],
            },
            normal: {
              barBorderRadius: [0, 20, 20, 0],
              color: new echarts.graphic.LinearGradient(
                0,
                0,
                1,
                0,
                [
                  {
                    offset: 0,
                    color: "rgba(2, 22, 80, 0.2)", // 0% 处的颜色
                  },
                  {
                    offset: 1,
                    color: "rgba(0, 255, 120, 0.8)", // 100% 处的颜色
                  },
                ],
                false
              ),
            },
          },
          label: {
            normal: {
              show: false,
              formatter: "{c}",
              position: "insideRight",
              offset: [-2, 1.5],
              textStyle: {
                color: "#fff",
                fontSize: 10,
              },
            },
          },
        },
        {
          name: "累计造林面积(万公顷)",
          textStyle: {
            // 提示框浮层的文本样式。
            color: "#fff",
            fontStyle: "normal",
            fontWeight: "normal",
            fontFamily: "sans-serif",
            fontSize: 14,
          },
          type: "bar",
          barGap: "-100%",
          itemStyle: {
            color: "rgba(0,0,0,0)",
            borderColor: "#fff",
            padding: 0,
            emphasis: {
              barBorderRadius: [0, 20, 20, 0],
            },
            normal: {
              barBorderRadius: [0, 20, 20, 0],
              color: new echarts.graphic.LinearGradient(
                0,
                0,
                1,
                0,
                [
                  {
                    offset: 0,
                    color: "rgba(2, 30, 86, 0.1)", // 0% 处的颜色
                  },
                  {
                    offset: 1,
                    color: "rgba(255, 177, 102, 0.9)", // 100% 处的颜色
                  },
                ],
                false
              ),
            },
          },
          label: {
            normal: {
              show: false,
              lineHeight: 12,
              formatter: "{c}",
              position: "right",
              right: 0,
              textStyle: {
                color: "#fff",
                fontSize: 12,
              },
            },
          },
          z: -10,
          data: [1500, 1482, 1432, 1236],
        },
      ],
      barCategoryGap: "60%",
    };
    // 使用刚指定的配置项和数据显示图表。
    myChart.setOption(option);
  },
};
</script>

<style>
#leftBarChart {
  width: 350px;
  height: 411px;
  margin: 0px auto;
}
</style>