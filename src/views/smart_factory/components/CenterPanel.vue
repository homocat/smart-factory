<script setup>
import echarts from "@/plugins/echarts";
import { onMounted } from "vue";
import ChartTable from "@/views/smart_factory/components/ChartTable.vue";

onMounted(() => {
  let dom1 = document.getElementById("charts");
  let myChart = echarts.init(dom1, null, {
    renderer: "canvas",
    useDirtyRect: false
  });
  let app1 = {};

  let option;

  let categories = (function () {
    let now = new Date();
    let res = [];
    let len = 10;
    while (len--) {
      res.unshift(now.toLocaleTimeString().replace(/^\D*/, ""));
      now = new Date(+now - 2000);
    }
    return res;
  })();
  let categories2 = (function () {
    let res = [];
    let len = 10;
    while (len--) {
      res.push(10 - len - 1);
    }
    return res;
  })();
  let data = (function () {
    let res = [];
    let len = 10;
    while (len--) {
      res.push(Math.round(Math.random() * 1000));
    }
    return res;
  })();
  let data2 = (function () {
    let res = [];
    let len = 0;
    while (len < 10) {
      res.push(+(Math.random() * 10 + 5).toFixed(1));
      len++;
    }
    return res;
  })();
  option = {
    // tooltip: {
    //   trigger: "axis",
    //   axisPointer: {
    //     type: "cross",
    //     label: {
    //       backgroundColor: "#283b56"
    //     }
    //   }
    // },
    legend: {},
    dataZoom: {
      show: false,
      start: 0,
      end: 100
    },
    xAxis: [
      {
        type: "category",
        boundaryGap: true,
        data: categories
      },
      {
        type: "category",
        boundaryGap: true,
        data: categories2
      }
    ],
    yAxis: [
      {
        type: "value",
        scale: true,
        name: "Price",
        max: 30,
        min: 0,
        boundaryGap: [0.2, 0.2]
      },
      {
        type: "value",
        scale: true,
        name: "Order",
        max: 1200,
        min: 0,
        boundaryGap: [0.2, 0.2]
      }
    ],
    series: [
      {
        name: "通过质检数",
        type: "bar",
        xAxisIndex: 1,
        yAxisIndex: 1,
        data: data
      },
      {
        name: "不良率t s",
        type: "line",
        data: data2
      }
    ]
  };
  app1.count = 11;
  setInterval(function () {
    let axisData = new Date().toLocaleTimeString().replace(/^\D*/, "");
    data.shift();
    data.push(Math.round(Math.random() * 1000));
    data2.shift();
    data2.push(+(Math.random() * 10 + 5).toFixed(1));
    categories.shift();
    categories.push(axisData);
    categories2.shift();
    categories2.push(app1.count++);
    myChart.setOption({
      xAxis: [
        {
          data: categories
        },
        {
          data: categories2
        }
      ],
      series: [
        {
          data: data
        },
        {
          data: data2
        }
      ]
    });
  }, 2100);

  if (option && typeof option === "object") {
    myChart.setOption(option);
  }

  window.addEventListener("resize", myChart.resize);

  let dom = document.getElementById("charts1");
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

  window.addEventListener("resize", myChart1.resize);
});
</script>

<template>
  <div class="flex flex-col justify-center items-center flex-1 m-[1rem]0">
    <div
      class="flex flex-row justify-center items-center bg-cover bg-[url('src/assets/framework/preview-6.png')] w-[100%] h-1/5 mb-[1rem]"
    >
      <div class="flex text-white">
        <img alt="" src="/src/assets/framework/preview-17.png" />
        <div class="flex ml-2 flex-col">
          <span>当日产量</span>
          <span>147,164件</span>
        </div>
      </div>
      <div class="flex ml-[5rem] text-white">
        <img alt="" src="/src/assets/framework/preview-17.png" />
        <div class="flex flex-col">
          <span>当月产量</span>
          <span>147,164件</span>
        </div>
      </div>
      <div class="flex ml-[5rem] text-white">
        <img alt="" src="/src/assets/framework/preview-10.png" />
        <div class="flex mx-2 flex-col">
          <span>目标达成率</span>
          <span>83%</span>
        </div>
      </div>
      <div class="flex ml-[5rem] text-white">
        <img alt="" src="/src/assets/framework/preview-7.png" />
        <div class="flex flex-col">
          <span>越投入产出</span>
          <span>74%</span>
        </div>
      </div>
    </div>
    <div class="w-[100%] flex-1 mb-[1rem]">
      <div
        class="flex flex-row justify-between bg-cover bg-[url('src/assets/framework/preview-1.png')] p-[0.5rem] text-white"
      >
        <span class="ml-[4rem] mt-[0.5rem] font-bold"> 产量与不良率统计 </span>
        <div
          class="flex justify-end pr-[1.5rem] pt-[0.2rem] items-center text-sm w-[8rem] h-[2rem] bg-cover bg-[url('src/assets/framework/preview-9.png')]"
        >
          实时看班
        </div>
      </div>
      <div id="charts" class="h-[80%] w-[100%]" />
    </div>
    <div class="w-[100%] h-[15rem] text-white">
      <div
        class="flex flex-row justify-start items-center font-bold pl-[5rem] bg-cover h-[3rem] bg-[url('src/assets/framework/preview-1.png')] p-[0.5rem] text-white"
      >
        设备监控
      </div>
      <div class="flex flex-row justify-center h-[100%}">
        <div
          id="charts1"
          class="w-[15rem] h-[15rem] bg-[url('src/assets/framework/preview-15.png')] bg-cover"
        />
        <ChartTable />
      </div>
    </div>
  </div>
</template>
