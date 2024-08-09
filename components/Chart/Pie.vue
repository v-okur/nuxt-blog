<template>
  <div ref="chart" :style="{ width: '100%', height: '400px' }"></div>
</template>

<script>
import { ref, onMounted, onBeforeUnmount } from "vue";
import * as echarts from "echarts/core";
import { PieChart } from "echarts/charts";
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent,
} from "echarts/components";
import { CanvasRenderer } from "echarts/renderers";

echarts.use([
  TitleComponent,
  TooltipComponent,
  LegendComponent,
  PieChart,
  CanvasRenderer,
]);

export default {
  name: "PieChartComponent",
  props: {
    options: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    const chart = ref(null);
    const chartInstance = ref(null);

    onMounted(() => {
      chartInstance.value = echarts.init(chart.value);
      chartInstance.value.setOption(props.options);
    });

    onBeforeUnmount(() => {
      if (chartInstance.value) {
        chartInstance.value.dispose();
      }
    });

    return {
      chart,
    };
  },
};
</script>

<style scoped>
/* İsteğe bağlı: Bileşen için stil ekleyebilirsiniz */
</style>
