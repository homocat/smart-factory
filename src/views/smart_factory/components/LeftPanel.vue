<script lang="ts" setup>
import { onMounted } from "vue";
import echarts from "@/plugins/echarts";
import ChartTable from "./ChartTable.vue";

onMounted(() => {
  let dom = document.getElementById("chart-container");
  let myChart = echarts.init(dom, null, {
    renderer: "canvas",
    useDirtyRect: false
  });
  let app = {};

  let option;

  option = {
    tooltip: {
      trigger: "axis"
    },
    legend: {
      data: ["Rainfall", "Evaporation"]
    },
    calculable: true,
    xAxis: [
      {
        type: "category",
        // prettier-ignore
        data: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
      }
    ],
    yAxis: [
      {
        type: "value"
      }
    ],
    series: [
      {
        name: "Rainfall",
        type: "bar",
        data: [
          2.0, 4.9, 7.0, 23.2, 25.6, 76.7, 135.6, 162.2, 32.6, 20.0, 6.4, 3.3
        ],
        markPoint: {
          data: [
            { type: "max", name: "Max" },
            { type: "min", name: "Min" }
          ]
        },
        markLine: {
          data: [{ type: "average", name: "Avg" }]
        }
      },
      {
        name: "Evaporation",
        type: "bar",
        data: [
          2.6, 5.9, 9.0, 26.4, 28.7, 70.7, 175.6, 182.2, 48.7, 18.8, 6.0, 2.3
        ],
        markPoint: {
          data: [
            { name: "Max", value: 182.2, xAxis: 7, yAxis: 183 },
            { name: "Min", value: 2.3, xAxis: 11, yAxis: 3 }
          ]
        },
        markLine: {
          data: [{ type: "average", name: "Avg" }]
        }
      }
    ]
  };

  if (option && typeof option === "object") {
    myChart.setOption(option);
  }

  // window.addEventListener('resize', myChart.resize);
});
</script>

<template>
  <div class="flex flex-col w-1/5 h-auto ml-[1rem] text-white">
    <div class="bg-[url('src/assets/framework/preview-1.png')] pl-[3rem]">
      一次通过率
    </div>
    <div class="h-1/3">
      <ChartTable />
    </div>
    <div class="h-1/3">
      <div class="bg-[url('src/assets/framework/preview-1.png')] pl-[3rem]">
        未齐套统计
      </div>
      <ChartTable />
    </div>
    <div class="h-1/3">
      <div id="chart-container" class="w-[100%] h-[100%]" />
    </div>
  </div>
</template>
