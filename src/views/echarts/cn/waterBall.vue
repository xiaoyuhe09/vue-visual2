<template>
  <div ref="myChart" id="waterBall"></div>
</template>

<script>
import * as echarts from "echarts";
import "echarts-liquidfill";
export default {
  mounted() {
    let myChart = echarts.init(this.$refs.myChart);
    let yearlist = ["1988", "1994", "2000", "2004", "2009", "2014", "2021"];
    let datalist = [0.14, 0.17, 0.18, 0.2, 0.27, 0.29, 0.32];
    let datalist1 = [0.15, 0.18, 0.19, 0.21, 0.28, 0.3, 0.33];
    let datalist2 = [0.13, 0.16, 0.17, 0.22, 0.26, 0.28, 0.31];
    let i = 0;
    let option = {
      title: {
        show: true,
        text: yearlist[0] + "年森林覆盖率",
        top: "center",
        left: "center",
        textStyle: {
          color: "#fff",
          fontSize: 24,
        },
      },
      series: [
        {
          type: "liquidFill", //水位图
          radius: "80%", //显示比例
          center: ["50%", "50%"], //中心点
          amplitude: 20, //水波振幅
          data: [datalist[0]], // data个数代表波浪数
          color: ["#23cc72"], //波浪颜色
          backgroundStyle: {
            borderWidth: 1, //外边框
            borderColor: "#23cc72", //边框颜色
            color: "#485C6D", //边框内部填充部分颜色
          },
          label: {
            //标签设置
            normal: {
              position: ["50%", "30%"],
              formatter: datalist[0], //显示文本,
              textStyle: {
                fontSize: "52px", //文本字号,
                color: "#23cc72",
              },
            },
          },
          // outline: {
          //     show: false,//最外层边框显示控制
          // },
        },
      ],
    };
    setInterval(function getRes() {
      i++;
      if (i == 7) {
        i = 0;
      }
      myChart.setOption({
        title: {
          show: true,
          text: yearlist[i] + "年森林覆盖率",
          top: "center",
          left: "center",
          textStyle: {
            color: "#fff",
            fontSize: 24,
          },
        },
        series: [
          {
            type: "liquidFill", //水位图
            radius: "80%", //显示比例
            center: ["50%", "50%"], //中心点
            amplitude: 20, //水波振幅
            data: [datalist[i], datalist1[i], datalist2[i]], // data个数代表波浪数
            color: ["#23cc72"], //波浪颜色
            backgroundStyle: {
              borderWidth: 1, //外边框
              borderColor: "#23cc72", //边框颜色
              color: "#485C6D", //边框内部填充部分颜色
            },
            label: {
              //标签设置
              normal: {
                position: ["50%", "30%"],
                formatter: datalist[i], //显示文本,
                textStyle: {
                  fontSize: "52px", //文本字号,
                  color: "#23cc72",
                },
              },
            },
            // outline: {
            //     show: false,//最外层边框显示控制
            // },
          },
        ],
      });
    }, 1500);
    myChart.setOption(option);
  },
};
</script>

<style>
#waterBall {
  width: 350px;
  height: 300px;
  margin: 0px auto;
  /* padding-top: 10px; */
  /* border: 2px solid red;
  background-color: #110839; */
}
</style>