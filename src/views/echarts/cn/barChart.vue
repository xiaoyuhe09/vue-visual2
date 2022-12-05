<template>
  <!-- <dv-border-box-1> -->
  <div ref="myChart" id="barChart"></div>
  <!-- </dv-border-box-1> -->
</template>

<script>
import * as echarts from "echarts";
// import Bus from "@/bus.js"
export default {
  mounted() {
    let myChart = echarts.init(this.$refs.myChart);
    let yearlist = ["1988", "1994", "2000", "2004", "2009", "2014", "2021"];
    var dataList = [
      "林业用地面积",
      "森林面积",
      "人工林面积",
      "荒漠化土地面积",
      "沙化土地面积",
      "全国水土流失面积",
    ];
    // myChart.on("timelinechanged", "timeline", (parmas)=>{
    //     console.log(parmas.currentIndex)
    // })

    var option = {
      timeline: {
        axisType: "category",
        autoPlay: true,
        playInterval: 1500,
        data: yearlist,
        label: {
          fontSize: 18,
        },
      },
      baseOption: {
        dataset: {
          source: [
            [
              "year",
              "林业用地面积",
              "森林面积",
              "人工林面积",
              "荒漠化土地面积",
              "沙化土地面积",
              "全国水土流失面积",
            ],
            [
              "1988",
              "232.1272",
              "133.642",
              "41.039",
              "271.2",
              "180.31",
              "346.53",
            ],
            [
              "1994",
              "263.295",
              "158.941",
              "46.667",
              "267.4",
              "177.69",
              "338.07",
            ],
            [
              "2000",
              "299.2048",
              "174.9092",
              "53.2573",
              "263.62",
              "173.97",
              "335.53",
            ],
            [
              "2004",
              "305.9041",
              "195.4522",
              "61.6884",
              "262.37",
              "173.11",
              "356.92",
            ],
            [
              "2009",
              "312.59",
              "207.6873",
              "69.3338",
              "259.95",
              "171.13",
              "294.91",
            ],
            [
              "2014",
              "323.6855",
              "220.4462",
              "80.031",
              "261.16",
              "172.12",
              "294.9",
            ],
            [
              "2021",
              "326.9871",
              "222.6948",
              "80.8473",
              "261.16",
              "172.12",
              "269.27",
            ],
          ],
        },
        title: {
          text: "1988年中国森林资源概况",
          left: "center",
          textStyle: {
            fontSize: 24,
            color: "#fff",
          },
        },
        tooltip: {
          show: true,
          trigger: "axis",
        },
        toolbox: {
          show: false,
          feature: {
            saveAsImage: {},
          },
        },
        legend: {},
        grid: {
          left: "1%",
          bottom: "15%",
          containLabel: true,
        },
        yAxis: [
          {
            type: "category",
            data: dataList,
            axisPointer: {
              type: "shadow",
            },
            axisLabel: {
              fontSize: 15,
              color: "#fff",
            },
          },
        ],
        xAxis: [
          {
            name: "百万公顷",
            type: "value",
            nameTextStyle: {
              fontSize: 10,
              color: "#fff",
            },
            axisLabel: {
              fontSize: 15,
              color: "#fff",
            },
          },
        ],
        series: [
          {
            //name: 'GDP',
            type: "bar",
            seriesLayoutBy: "row",
            encode: {
              x: "year",
              y: "1988",
            },
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
                        color: "rgba(0, 255, 120, 0.2)", // 0% 处的颜色
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
          },
        ],
      },
      options: [],
    };

    for (var n = 0; n < yearlist.length; n++) {
      option.options.push({
        title: {
          show: true,
          text: yearlist[n] + "中国森林资源概况",
          left: "center",
          textStyle: {
            fontSize: 24,
          },
        },
        series: [
          {
            type: "bar",
            seriesLayoutBy: "row",
            encode: {
              y: "year",
              x: yearlist[n],
            },
          },
        ],
      });
    }

    // 使用刚指定的配置项和数据显示图表。
    myChart.setOption(option);
  },
};
</script>

<style>
#barChart {
  width: 762px;
  height: 412px;
  margin: 0px auto;
  /* margin: 100px; */
  margin-top: 45px;
  /* border: 2px solid red;
  background-color: #110839; */
}
</style>

<!-- <template>
    <div ref="myChart" id="barChart"></div> 
</template>

<script>
import { inject,Mounted } from 'vue';
export default {
    setup(){
        let $echarts=inject("echarts")
        let $http=inject("axios")

        async function getState(){
        let oneData = await $http({url:"http://127.0.0.1:8888/one/data"})
        console.log(oneData.data.chartData.chartData)
        }

        Mounted(()=>{
            let myChart=$echarts.init(document.getElementById("barChart"))

        })
    }
}
</script>

<style>
</style> -->