<template>
  <div ref="myChart" id="chinaMap"></div>
</template>
    
    <script>
import * as echarts from "echarts";
import { mapData } from "@/assets2/mapData";
// import $ from 'jquery'
export default {
  mounted() {
    let myChart = echarts.init(this.$refs.myChart);
    //注册地图名
    echarts.registerMap("china", mapData);
    // var provinces = {
    //     '上海': '@/asset/mapJS/shanghai.json',
    //     '河北': '@/asset/mapJS/hebei.json',
    //     '山西': '@/asset/mapJS/shanxi1.json',
    //     '内蒙古': '@/asset/mapJS/neimenggu.json',
    //     '辽宁': '@/asset/mapJS/liaoning.json',
    //     '吉林': '@/asset/mapJS/jilin.json',
    //     '黑龙江': '@/asset/mapJS/heilongjiang.json',
    //     '江苏': '@/asset/mapJS/jiangsu.json',
    //     '浙江': '@/asset/mapJS/zhejiang.json',
    //     '安徽': '@/asset/mapJS/anhui.json',
    //     '福建': '@/asset/mapJS/fujian.json',
    //     '江西': '@/asset/mapJS/jiangxi.json',
    //     '山东': '@/asset/mapJS/shandong.json',
    //     '河南': '@/asset/mapJS/henan.json',
    //     '湖北': '@/asset/mapJS/hubei.json',
    //     '湖南': '@/asset/mapJS/hunan.json',
    //     '广东': '@/asset/mapJS/guangdong.json',
    //     '广西': '@/asset/mapJS/guangxi.json',
    //     '海南': '@/asset/mapJS/hainan.json',
    //     '四川': '@/asset/mapJS/sichuan.json',
    //     '贵州': '@/asset/mapJS/guizhou.json',
    //     '云南': '@/asset/mapJS/yunnan.json',
    //     '西藏': '@/asset/mapJS/xizang.json',
    //     '陕西': '@/asset/mapJS/shanxi.json',
    //     '甘肃': '@/asset/mapJS/gansu.json',
    //     '青海': '@/asset/mapJS/qinghai.json',
    //     '宁夏': '@/asset/mapJS/ningxia.json',
    //     '新疆': '@/asset/mapJS/xinjiang.json',
    //     '北京': '@/asset/mapJS/beijing.json',
    //     '天津': '@/asset/mapJS/tianjin.json',
    //     '重庆': '@/asset/mapJS/chongqing.json',
    //     '香港': '@/asset/mapJS/xianggang.json',
    //     '澳门': '@/asset/mapJS/aomen.json',
    //     '台湾': '@/asset/mapJS/taiwan.json'
    // };

    // //各省份的数据
    // var allData = [{
    //     name: '北京'
    // }, {
    //     name: '天津'
    // }, {
    //     name: '上海'
    // }, {
    //     name: '重庆'
    // }, {
    //     name: '河北'
    // }, {
    //     name: '河南'
    // }, {
    //     name: '云南'
    // }, {
    //     name: '辽宁'
    // }, {
    //     name: '黑龙江'
    // }, {
    //     name: '湖南'
    // }, {
    //     name: '安徽'
    // }, {
    //     name: '山东'
    // }, {
    //     name: '新疆'
    // }, {
    //     name: '江苏'
    // }, {
    //     name: '浙江'
    // }, {
    //     name: '江西'
    // }, {
    //     name: '湖北'
    // }, {
    //     name: '广西'
    // }, {
    //     name: '甘肃'
    // }, {
    //     name: '山西'
    // }, {
    //     name: '内蒙古'
    // }, {
    //     name: '陕西'
    // }, {
    //     name: '吉林'
    // }, {
    //     name: '福建'
    // }, {
    //     name: '贵州'
    // }, {
    //     name: '广东'
    // }, {
    //     name: '青海'
    // }, {
    //     name: '西藏'
    // }, {
    //     name: '四川'
    // }, {
    //     name: '宁夏'
    // }, {
    //     name: '海南'
    // }, {
    //     name: '台湾'
    // }, {
    //     name: '香港'
    // }, {
    //     name: '澳门'
    // }];

    // // loadMap('@/asset/china.json', 'china');
    // var timeFn = null;

    // //单击切换到省级地图，当mapCode有值,说明可以切换到下级地图
    // myChart.on('click', function(params) {
    //     clearTimeout(timeFn);
    //     //由于单击事件和双击事件冲突，故单击的响应事件延迟250毫秒执行
    //     timeFn = setTimeout(function() {
    //         var name = params.name; //地区name
    //         var mapCode = provinces[name]; //地区的json数据
    //         if (!mapCode) {
    //             alert('无此区域地图显示');
    //             return;
    //         }

    //         loadMap(mapCode, name);

    //     }, 250);
    // });

    // // 绑定双击事件，返回全国地图
    // // myChart.on('dblclick', function(params) {
    // //     //当双击事件发生时，清除单击事件，仅响应双击事件
    // //     clearTimeout(timeFn);

    // //     //返回全国地图
    // //     loadMap('@/asset/china.json', 'china');
    // // });

    // //  获取对应的json地图数据，然后向echarts注册该区域的地图，最后加载地图信息
    // // @params {String} mapCode:json数据的地址
    // // @params {String} name: 地图名称

    // function loadMap(mapCode, name) {
    //     $.get(mapCode, function(data) {
    //         if (data) {
    //             echarts.registerMap(name, data);
    //             let option = {
    //                 // tooltip: {
    //                 //     show: true,
    //                 //     formatter: function(params) {
    //                 //         if (params.data) return params.name + '：' + params.data['value']
    //                 //     },
    //                 // },
    //                 // visualMap: {
    //                 //     type: 'continuous',
    //                 //     text: ['', ''],
    //                 //     showLabel: true,
    //                 //     left: '50',
    //                 //     min: 0,
    //                 //     max: 100,
    //                 //     inRange: {
    //                 //         color: ['#edfbfb', '#b7d6f3', '#40a9ed', '#3598c1', '#215096', ]
    //                 //     },
    //                 //     splitNumber: 0
    //                 // },
    //                 series: [{
    //                     name: 'MAP',
    //                     type: 'map',
    //                     mapType: name,
    //                     selectedMode: 'false',//是否允许选中多个区域
    //                     label: {
    //                         normal: {
    //                             show: true
    //                         },
    //                         emphasis: {
    //                             show: true
    //                         }
    //                     },
    //                     data: allData
    //                 }]
    //             };
    //             myChart.setOption(option);
    //             // curMap = {
    //             //     mapCode: mapCode,
    //             //     mapName: name
    //             // };
    //         } else {
    //             alert('无法加载该地图');
    //         }
    //     });
    // }
    let option = {
      // visualMap: {
      //         min: 0,
      //         max: 300,
      //         left: 'left',
      //         top: 'bottom',
      //         text: ['高', '低'],
      //         calculable: true,
      //         // seriesIndex: [1],
      //         inRange: {
      //             color: ['#0c3653','rgba(255, 177, 102)']
      //         },
      //         show: true
      //     },
      geo: {
        //地理坐标组件
        type: "map",
        map: "china",
        roam: true,
        zoom: 1.6,
        center: [105.405285, 33.904989],
        label: {
          show: true,
          color: "#fff",
          fontSize: 10,
        },
        scaleLimit: {
          //滚轮缩放的极限控制
          min: 1,
          max: 3,
        },

        itemStyle: {
          normal: {
            areaColor: "#0c3653",
            borderColor: "rgba(0, 255, 255)",
            borderWidth: 1.8,
          },
          emphasis: {
            areaColor: "#56b1da",
            label: {
              show: false,
              color: "#fff",
            },
          },
        },
      },
      // tooltip:{
      //     show:true

      // },
      //     series:[
      //         {
      //             type:"effectScatter",
      //             data:[
      //                 {
      //                     name:"呼和浩特市",
      //                     value:[
      //                     111.670801,40.818311,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"包头市",
      //                     value:[
      //                     109.840405,40.658168,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"乌海市",
      //                     value:[
      //                     106.825563,39.673734,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"赤峰市",
      //                     value:[
      //                     122.263119,43.617429,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"通辽市",
      //                     value:[
      //                     108.948024,34.263161,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"鄂尔多斯市",
      //                     value:[
      //                     109.99029,39.817179,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"呼伦贝尔市",
      //                     value:[
      //                     119.758168,49.215333,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"巴彦淖尔市",
      //                     value:[
      //                     107.416959,40.757402,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"乌兰察布市",
      //                     value:[
      //                     113.114543,41.034126,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"兴安盟",
      //                     value:[
      //                     122.070317,46.076268,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"锡林郭勒盟",
      //                     value:[
      //                     116.090996,43.944018,2000
      //                     ]
      //                 },
      //                 {
      //                     name:"阿拉善盟",
      //                     value:[
      //                     105.706422,38.844814,2000
      //                     ]
      //                 }
      //             ],
      //             coordinateSystem:"geo",
      //             symbolSize:15,
      //         },
      //         {
      //             type:"effectScatter",
      //             data:[
      //                 {
      //                     name:"陕西省",
      //                     value:[
      //                     108.948024,34.263161,2000
      //                     ]
      //                 }
      //             ],
      //             coordinateSystem:"geo",
      //             symbolSize:6,
      //         },
      //         {
      //             type:"effectScatter",
      //             data:[
      //                 {
      //                     name:"新疆维吾尔自治区",
      //                     value:[
      //                     87.617733,43.792818,2000
      //                     ]
      //                 }
      //             ],
      //             coordinateSystem:"geo",
      //             symbolSize:25,
      //         }
      //     ]
    };
    myChart.setOption(option);
  },
};
</script>
    
    <style>
#chinaMap {
  width: 662px;
  height: 400px;
  margin: 0 auto;
}
</style>