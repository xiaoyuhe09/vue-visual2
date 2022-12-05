<template>
  <div id="index" ref="appRef">
    <div class="bg">
      <dv-loading v-if="loading">Loading...</dv-loading>
      <div v-else class="host-body">
        <div class="d-flex jc-center">
          <dv-decoration-10 class="dv-dec-10" />
          <div class="d-flex jc-center">
            <dv-decoration-8 class="dv-dec-8" :color="decorationColors" />
            <div class="title">
              <span class="title-text">{{ title }}</span>
              <dv-decoration-6
                class="dv-dec-6"
                :reverse="true"
                :color="['#50e3c2', '#67a1e5']"
              />
            </div>
            <dv-decoration-8
              class="dv-dec-8"
              :reverse="true"
              :color="decorationColors"
            />
          </div>
          <dv-decoration-10 class="dv-dec-10-s" />
        </div>

        <!-- 第二行 -->
        <div class="d-flex jc-between px-2">
          <div class="d-flex aside-width">
            <div class="react-left ml-4 react-l-s">
              <span class="react-before"></span>
              <span class="text">{{ subtitle[0] }}</span>
            </div>
            <div class="react-left ml-3">
              <span class="text">{{ subtitle[1] }}</span>
            </div>
          </div>
          <div class="d-flex aside-width">
            <div class="react-right bg-color-blue mr-3">
              <span class="text fw-b">{{ subtitle[2] }}</span>
            </div>
            <div class="react-right mr-4 react-l-s">
              <span class="react-after"></span>
              <span class="text">
                {{ timeInfo.dateYear }} {{ timeInfo.dateWeek }}
                {{ timeInfo.dateDay }}
              </span>
            </div>
          </div>
        </div>

        <div class="body-box">
          <!-- 第三行数据 -->
          <div class="content-box">
            <div>
              <dv-border-box-11 title="树木种类分布">
                <pie-chart></pie-chart>
              </dv-border-box-11>
            </div>
            <div>
              <dv-border-box-12 style="padding-bottom: 35px">
                <!-- <center-left2 /> -->
                <cn-map />
              </dv-border-box-12>
            </div>
            <div class="waterball">
              <dv-border-box-12 style="padding-top: 50px">
                <!-- <center-left2 /> -->
                <water-ball />
              </dv-border-box-12>
            </div>
            <!-- 中间 -->
            <div>
              <center />
            </div>
            <!-- 中间 -->
            <div>
              <center-right1 />
            </div>
            <div>
              <dv-border-box-8 :reverse="true" style="padding-top: 100px"
                ><line-chart
              /></dv-border-box-8>
            </div>
            <dv-border-box-8
              style="width: 1000px; height: 500px"
              class="juege"
              :reverse="true"
            >
              <bar-chart></bar-chart>
            </dv-border-box-8>
            <dv-border-box-5
              style="padding-top: 50px"
              :reverse="true"
              :color="['rgb(32, 98, 131)', 'rgb(32, 98, 101)']"
            >
              <left-bar-chart />
            </dv-border-box-5>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive, onMounted, onUnmounted } from "vue";
import { formatTime } from "@/utils/index";
import { WEEK } from "@/constant/index";
import useDraw from "@/utils/useDraw";
import { title, subtitle, moduleInfo } from "@/constant/index";
import CenterLeft1 from "../centerLeft1/index.vue";
import CenterLeft2 from "../centerLeft2/index.vue";
import Center from "../center/index.vue";
import CenterRight1 from "../centerRight1/index.vue";
import CenterRight2 from "../centerRight2/index.vue";
import BottomLeft from "../bottomLeft/index.vue";
import BottomRight from "../bottomRight/index.vue";
import PieChart from "../echarts/cn/pieChart.vue";
import LineChart from "../echarts/cn/lineChart.vue";
import BarChart from "../echarts/cn/barChart.vue";
import LeftBarChart from "../echarts/cn/leftbarChart.vue";
import WaterBall from "../echarts/cn/waterBall.vue";
import CnMap from "../echarts/cn/chinaMap.vue";

export default defineComponent({
  components: {
    CenterLeft1,
    CenterLeft2,
    Center,
    CenterRight1,
    CenterRight2,
    BottomLeft,
    BottomRight,
    PieChart,
    LineChart,
    BarChart,
    LeftBarChart,
    WaterBall,
    CnMap,
  },
  setup() {
    // * 颜色
    const decorationColors = ["#568aea", "#000000"];
    // * 加载标识
    const loading = ref<boolean>(true);
    // * 时间内容
    const timeInfo = reactive({
      setInterval: 0,
      dateDay: "",
      dateYear: "",
      dateWeek: "",
    });
    // * 适配处理
    const { appRef, calcRate, windowDraw, unWindowDraw } = useDraw();
    // 生命周期
    onMounted(() => {
      cancelLoading();
      handleTime();
      // todo 屏幕适应
      windowDraw();
      calcRate();
    });

    onUnmounted(() => {
      unWindowDraw();
      clearInterval(timeInfo.setInterval);
    });

    // methods
    // todo 处理 loading 展示
    const cancelLoading = () => {
      setTimeout(() => {
        loading.value = false;
      }, 500);
    };

    // todo 处理时间监听
    const handleTime = () => {
      timeInfo.setInterval = setInterval(() => {
        const date = new Date();
        timeInfo.dateDay = formatTime(date, "HH: mm: ss");
        timeInfo.dateYear = formatTime(date, "yyyy-MM-dd");
        timeInfo.dateWeek = WEEK[date.getDay()];
      }, 1000);
    };

    // return
    return {
      loading,
      timeInfo,
      appRef,
      title,
      subtitle,
      moduleInfo,
    };
  },
});
</script>

<style lang="scss" scoped>
@import "@/assets/scss/index.scss";
.juege {
  /* border-bottom: 1px solid tomato; */
}
.linechart {
  height: 500px;
  width: 500px;
  border-bottom: 1px solid pink;
}
.waterball {
  width: 500px;
  border-right: 2px solid rgb(32, 98, 191);
}
</style>
