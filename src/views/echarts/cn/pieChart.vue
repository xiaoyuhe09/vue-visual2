

<template>
  <div ref="myChart" id="pieChart"></div>
  <slot></slot>
</template>

<script>
import * as echarts from "echarts";
export default {
  mounted() {
    let myChart = echarts.init(this.$refs.myChart);
    let yearlist = ["1988", "1994", "2000", "2004", "2009", "2014", "2021"];
    // const series = [['40','41','43','45','47','48','49'],['40','41','43','45','47','48','49'],['40','41','43','45','47','48','49'],['40','41','43','45','47','48','49'],['40','41','43','45','47','48','49']]
    let tree1 = [40, 41, 42, 31, 26, 46, 49];
    let tree2 = [38, 34, 35, 36, 37, 38, 39];
    let tree3 = [32, 35, 37, 32, 31, 30, 39];
    let tree4 = [20, 22, 23, 21, 27, 28, 29];
    let tree5 = [18, 17, 15, 14, 19, 17, 18];
    let i = 0;
    let option = {
      title: {
        top: "top",
        left: "center",
        show: true,
        text: yearlist[0] + "",
        textStyle: {
          color: "#fff",
          fontSize: 24,
        },
      },
      legend: {
        top: "center",
        left: 1,
        orient: "vertical",
        textStyle: {
          color: "#fff",
        },
      },
      toolbox: {
        show: true,
      },
      tooltip: {
        trigger: "item",
        backgroundColor: "rgba(47,37,198,0.75)",
        borderColor: "#2880FF",
        borderWidth: 1,
        textStyle: {
          color: "#fff",
        },
      },
      series: [
        {
          name: "Nightingale Chart",
          type: "pie",
          radius: ["40%", "75%"],
          center: ["50%", "50%"],
          roseType: "area",
          label: { show: false },
          labelLine: { show: false },
          selectedOffset: 30,
          selectedMode: true,
          itemStyle: {
            borderRadius: 8,
          },
          data: [
            { value: tree1[i], name: "马尾松" },
            { value: tree2[i], name: "云南松" },
            { value: tree3[i], name: "思茅松" },
            { value: tree4[i], name: "柏木" },
            { value: tree5[i], name: "巴山松" },
          ],
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
          top: "top",
          left: "center",
          show: true,
          text: yearlist[i] + "",
          textStyle: {
            color: "#fff",
            fontSize: 24,
          },
        },
        series: [
          {
            name: "Nightingale Chart",
            type: "pie",
            radius: ["40%", "75%"],
            center: ["50%", "50%"],
            roseType: "area",
            label: { show: false },
            labelLine: { show: false },
            selectedOffset: 30,
            selectedMode: true,
            itemStyle: {
              borderRadius: 8,
            },
            data: [
              { value: tree1[i], name: "马尾松" },
              { value: tree2[i], name: "云南松" },
              { value: tree3[i], name: "思茅松" },
              { value: tree4[i], name: "柏木" },
              { value: tree5[i], name: "巴山松" },
            ],
          },
        ],
      });
    }, 1500);
    myChart.setOption(option);
  },
};
</script>

<style>
#pieChart {
  width: 350px;
  height: 300px;
  margin: 0px auto;
  padding-top: 100px;
  padding-left: 30px;
  /* border: 2px solid red;
    background-color: #110839; */
}
</style>