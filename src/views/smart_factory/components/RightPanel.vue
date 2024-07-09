<script lang="ts" setup>
import { onMounted } from "vue";
import echarts from "@/plugins/echarts";
import ChartTable from "@/views/smart_factory/components/ChartTable.vue";

onMounted(() => {
  let dom1 = document.getElementById("chart-container-right");
  let myChart = echarts.init(dom1, null, {
    renderer: "canvas",
    useDirtyRect: false
  });
  let app = {};

  let option;

  option = {
    xAxis: {
      type: "category",
      data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"]
    },
    yAxis: {
      type: "value"
    },
    series: [
      {
        data: [150, 230, 224, 218, 135, 147, 260],
        type: "line"
      }
    ]
  };

  if (option && typeof option === "object") {
    myChart.setOption(option);
  }

  let dom = document.getElementById("chart-container-right1");
  let myChart1 = echarts.init(dom, null, {
    renderer: "canvas",
    useDirtyRect: false
  });
  // let app = {};

  let option1 = {
    tooltip: {
      trigger: "item"
    },
    legend: {
      top: "5%",
      left: "center"
    },
    series: [
      {
        name: "Access From",
        type: "pie",
        radius: ["40%", "70%"],
        avoidLabelOverlap: false,
        padAngle: 5,
        itemStyle: {
          borderRadius: 10
        },
        label: {
          show: false,
          position: "center"
        },
        emphasis: {
          label: {
            show: true,
            fontSize: 40,
            fontWeight: "bold"
          }
        },
        labelLine: {
          show: false
        },
        data: [
          { value: 1048, name: "Search Engine" },
          { value: 735, name: "Direct" },
          { value: 580, name: "Email" },
          { value: 484, name: "Union Ads" },
          { value: 300, name: "Video Ads" }
        ]
      }
    ]
  };

  if (option1 && typeof option1 === "object") {
    myChart1.setOption(option1);
  }
});
</script>

<template>
  <div class="flex flex-col w-1/5 h-auto mr-[1rem] text-white">
    <div class="bg-[url('src/assets/framework/preview-1.png')] pl-[3rem]">
      投入产出监控
    </div>
    <div class="h-1/3">
      <ChartTable />
    </div>
    <div class="h-1/3">
      <div class="bg-[url('src/assets/framework/preview-1.png')] pl-[3rem]">
        成本控制
      </div>
      <div id="chart-container-right1" class="h-[100%] w-[100%]" />
    </div>
    <div class="h-1/3">
      <div class="bg-[url('src/assets/framework/preview-1.png')] pl-[3rem]">
        产能效率
      </div>
      <div id="chart-container-right" class="w-[100%] h-[100%]" />
    </div>
  </div>
</template>
